Лабораторно-практическая  работа   №  5. 
Тема «Использование  компонента  RichEdit». 
Цель:  Закрепить навыки применения  редактора RichEdit. Методические  рекомендации  и  ход  выполнения  работы. 
1.	Конструирование  формы.   
На  форму  помещаем следующие  компоненты:  панель (свойство  Dock  устанавливаем  в значение  Bottom)  и   редактор RichTextBox (свойство   Dock  устанавливаем  в  значение Fill).  На  панели  размещаем  2  списка  ComboBox (первый  будем  заполнять  программно,  а  второй  на  этапе  проектирования,  занеся  в  него  размеры  шрифтов,) ,  6   кнопок,  установив  для  них  свойство Text  соответственно: Форматировать, Список, Заголовок, Сохранить, Открыть, Закрыть 
Поместите 2  радиокнопки с заголовками TXT и RTF. Также добавьте невидимый компонент SaveFileDialog, OpenFileDialog. 
2.	Программирование  
Создать  обработчики   следующих  событий: 
	• 	Для  формы  Form_load,  в  который  помещаем  следующий  программный  код:  
 
// Заполнение comboBox1 системными шрифтами  foreach (FontFamily ff in FontFamily.Families) 
 { 
     comboBox1.Items.Add(ff.Name); 
 } 
 comboBox1.SelectedIndex = 0; // Выбрать первый шрифт 
 
 // Убедиться, что хотя бы один размер выбран  comboBox2.SelectedIndex = 0; 
 // Заполнить поле текстом.(можно в свойстве текст.)  richTextBox1.Text = "Первая строка текста.\n" + 
         "Вторая строка текста.\n" + 
         "Третья строка текста.\n" + 
         "Четвёртая строка текста.\n" + 
  "Пятая строка текста."; 
 
	• 	Щелчка  по  кнопке «Форматировать», поместив в него  программный  код:             
 
// Выделить весь текст  richTextBox1.SelectAll(); 
 
 // Установить выравнивание по левому краю 
 richTextBox1.SelectionAlignment = HorizontalAlignment.Left; 
 
 // Применить шрифт  if (comboBox1.SelectedItem != null) 
 { 
     string fontName = comboBox1.SelectedItem.ToString();      float fontSize = comboBox2.SelectedItem != null          ? float.Parse(comboBox2.SelectedItem.ToString()) 
         : 10f; 
 
     richTextBox1.SelectionFont = new Font(fontName, fontSize); 
 } 
 
 // Сброс выделения 
 richTextBox1.Select(0, 0); 
 
	• 	Щелчка  по  кнопке  «Список»,  поместив в него строку кода: 
 
 int start = richTextBox1.SelectionStart; 
 int length = richTextBox1.SelectionLength; 
 
 if (length == 0) 
     return; 
 
 string selectedText = richTextBox1.SelectedText; 
 string[] lines = selectedText.Split('\n');  for (int i = 0; i < lines.Length; i++) 
 {      if (!lines[i].StartsWith("• "))          lines[i] = "• " + lines[i]; 
 } 
 
 richTextBox1.SelectedText = string.Join("\n", lines); 
        
•	Щелчка  по  кнопке  «Заголовок»  поместив в него программный  код: 
 
float fontSize = 14f; 
if (comboBox2.SelectedItem != null) 
    fontSize = float.Parse(comboBox2.SelectedItem.ToString()); 
 
// Применить жирный и курсив 
FontStyle style = FontStyle.Bold | FontStyle.Italic; 
 
// Применить к выделенному тексту richTextBox1.SelectionFont = new Font(richTextBox1.SelectionFont.FontFamily, fontSize, style); 
 
•	*Щелчка  по  кнопке   «Сохранить» поместив в него программный  код: 
 if (!radioButton1.Checked && !radioButton2.Checked) 
{ 
    MessageBox.Show("Не выбран вариант сохранения", "Ошибка", MessageBoxButtons.OK, 
MessageBoxIcon.Warning); 
    return; 
} 
 
if (saveFileDialog1.ShowDialog() == DialogResult.OK) 
{ 
    string fileName = saveFileDialog1.FileName; 
 
    if (radioButton1.Checked) // TXT 
    { 
        // Сохранить как обычный текст 
        File.WriteAllText(fileName + ".txt", richTextBox1.Text, Encoding.UTF8); 
    } 
    else if (radioButton2.Checked) // RTF 
    { 
        // Сохранить как форматированный RTF         richTextBox1.SaveFile(fileName + ".rtf", RichTextBoxStreamType.RichText); 
