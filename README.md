Вы можете использовать метод EndInvoke для получения результата возращаемого методом BeginInvoke. В вашем случае он не нужен, так как BeginInvoke не возвращает результат. Однако, если вы хотите узнать, завершена ли операция, вы можете создать делегат AsyncCallback и передать его в метод BeginInvoke. В этом случае делегат будет вызван по завершении операции и вы можете выполнять дополнительные действия, например, обновить состояние пользовательского интерфейса. 

Например, таким образом можно очистить список и изменить заголовок формы:

```
// создаем делегат AsyncCallback
AsyncCallback callback = delegate(IAsyncResult asyncResult)
{
    // метод EndInvoke закончит выполнение начатой операции
    ListDataCom.EndInvoke(asyncResult);
    // код который выполнится после завершения операции
    this.Invoke((MethodInvoker)delegate
    {
        ListDataCom.Items.Clear();
        this.Text = "Данные очищены";
    });
};

// запускаем операцию в отдельном потоке
ListDataCom.BeginInvoke(callback);
```

Для сброса диалога введите команду /context

Чтобы вызвать метод очистки и заполнения ListBox в новом потоке, можно использовать класс `Task` из пространства имен System.Threading.Tasks. Не забудьте, что при обновлении элементов управления в другом потоке нужно использовать метод `Invoke` или `BeginInvoke` контроля, на котором происходят обновления.

Пример:

```
private void button1_Click(object sender, EventArgs e)
{
    // Запустить новый поток, в котором производятся обновления ListBox
    Task.Run(() =>
    {
        // Очистить ListBox
        Invoke((Action)(() => listBox1.Items.Clear()));

        // Заполнить ListBox новыми значениями
        string[] newValues = { "Первый элемент", "Второй элемент", "Третий элемент" };
        Invoke((Action)(() => listBox1.Items.AddRange(newValues)));
    });
}
```

В данном примере мы запускаем новый поток с помощью метода `Task.Run()`, который принимает делегат с кодом для выполнения в потоке. В этом делегате мы вызываем методы для очистки и заполнения ListBox, используя метод `Invoke` для обновления элемента управления в главном потоке.

Для сброса диалога введите команду /context
