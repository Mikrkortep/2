В React можно преобразовать JSON-файл в HTML-разметку, используя методы JavaScript. В данном примере мы будем использовать функциональные компоненты и хук `useState` для хранения данных из JSON-файла.

Допустим, у нас есть JSON-файл `data.json` с информацией о товарах:

```
[
  {
    "id": 1,
    "name": "Товар 1",
    "price": "100 руб."
  },
  {
    "id": 2,
    "name": "Товар 2",
    "price": "200 руб."
  }
]
```

Мы можем сделать следующее:

1. Загрузить данные из JSON-файла и сохранить их в состоянии компонента с помощью хука `useState`.
2. Использовать метод `map` для перебора элементов массива и создания HTML-блоков для каждого элемента.
3. Возвращать массив HTML-блоков из компонента.

```javascript
import React, { useState, useEffect } from 'react';
import data from './data.json';

function App() {
  const [products, setProducts] = useState([]);

  useEffect(() => {
    setProducts(data);
  }, []);

  return (
    <div>
      {products.map(product => (
        <div key={product.id}>
          <h2>{product.name}</h2>
          <p>{product.price}</p>
        </div>
      ))}
    </div>
  )
}

export default App;
```

Обратите внимание, что мы используем уникальный ключ `key` для каждого элемента, чтобы React мог оптимизировать рендеринг и избежать ошибок при изменении компонентов.

Таким образом, мы можем легко преобразовать JSON-файл в HTML-разметку с помощью React.

Для сброса диалога введите команду /context
