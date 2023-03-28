Для динамического изменения цвета в WPF можно использовать свойство Background у элемента управления. Вот пример кода на C#:

``` csharp
// Получаем элемент управления по его имени
var button = (Button)FindName("myButton");

// Создаем новый объект SolidColorBrush с желаемым цветом
var brush = new SolidColorBrush(Colors.Red);

// Присваиваем созданный объект к свойству Background элемента управления
button.Background = brush;
```

Также можно использовать анимацию для плавного изменения цвета. Вот пример XAML-кода:

``` xaml
<Button x:Name="myButton" Content="Нажми меня">
  <Button.Triggers>
    <EventTrigger RoutedEvent="Button.MouseEnter">
      <BeginStoryboard>
        <Storyboard>
          <ColorAnimation To="Red" Duration="0:0:0.5"
                          Storyboard.TargetProperty="(Button.Background).(SolidColorBrush.Color)"/>
        </Storyboard>
      </BeginStoryboard>
    </EventTrigger>
    <EventTrigger RoutedEvent="Button.MouseLeave">
      <BeginStoryboard>
        <Storyboard>
          <ColorAnimation To="White" Duration="0:0:0.5"
                          Storyboard.TargetProperty="(Button.Background).(SolidColorBrush.Color)"/>
        </Storyboard>
      </BeginStoryboard>
    </EventTrigger>
  </Button.Triggers>
</Button>
```

Этот код создает кнопку, которая при наведении мыши изменяет свой цвет на красный с помощью анимации, а при отведении мыши возвращает свой цвет в начальное состояние.

Для сброса диалога введите команду /context
