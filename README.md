# 2
Чтобы получить данные с SPI на STM32 с использованием SPI5, вам нужно выполнить следующие шаги:

1. Настроить порт SPI. Вы можете использовать функцию CubeMX или настроить порт SPI вручную. Например, если вы используете STM32CubeIDE, для настройки порта SPI5 можно использовать следующий код:

```
/* USER CODE BEGIN SPI5_MspInit 0 */

/* USER CODE END SPI5_MspInit 0 */
/* SPI5 parameter configuration*/
hspi5.Instance = SPI5;
hspi5.Init.Mode = SPI_MODE_MASTER;
hspi5.Init.Direction = SPI_DIRECTION_2LINES;
hspi5.Init.DataSize = SPI_DATASIZE_8BIT;
hspi5.Init.CLKPolarity = SPI_POLARITY_LOW;
hspi5.Init.CLKPhase = SPI_PHASE_1EDGE;
hspi5.Init.NSS = SPI_NSS_SOFT;
hspi5.Init.BaudRatePrescaler = SPI_BAUDRATEPRESCALER_2;
hspi5.Init.FirstBit = SPI_FIRSTBIT_MSB;
hspi5.Init.TIMode = SPI_TIMODE_DISABLE;
hspi5.Init.CRCCalculation = SPI_CRCCALCULATION_DISABLE;
hspi5.Init.CRCPolynomial = 10;
if (HAL_SPI_Init(&hspi5) != HAL_OK)
{
  Error_Handler();
}

/* USER CODE BEGIN SPI5_MspInit 1 */

/* USER CODE END SPI5_MspInit 1 */
```

2. Создать функцию для отправки данных через SPI. Например:

```
void SPI_SendData(SPI_HandleTypeDef *hspi, uint8_t *pData, uint16_t Size)
{
    HAL_SPI_Transmit(hspi, pData, Size, 100);
}
```

3. Создать функцию для чтения данных из SPI. Например:

```
uint8_t SPI_ReadData(SPI_HandleTypeDef *hspi, uint8_t *pData, uint16_t Size)
{
    HAL_SPI_Receive(hspi, pData, Size, 100);
}
```

4. Отправить команду гироскопа L3GD20H для чтения данных с регистра. Например:

```
uint8_t L3GD20H_Read_Reg(uint8_t reg)
{
    uint8_t value;

    HAL_GPIO_WritePin(SPI_CS_GPIO_Port, SPI_CS_Pin, GPIO_PIN_RESET); // низкий уровень на CS для выбора устройства

    uint8_t TxData[2] = {reg | 0x80, 0x00}; // отправляем адрес регистра, с битом чтения
    uint8_t RxData[2] = {0xFF, 0xFF};

    HAL_SPI_TransmitReceive(&hspi5, TxData, RxData, 2, 100); // отправляем данные по SPI, ожидаем 100 мс

    value = RxData[1]; // значение, полученное из регистра

    HAL_GPIO_WritePin(SPI_CS_GPIO_Port, SPI_CS_Pin, GPIO_PIN_SET); // высокий уровень на CS для снятия выделения с устройства

    return value;
}
```

5. Прочитать данные с гироскопа L3GD20H. Например:

```
uint16_t L3GD20H_Read_X_L()
{
    uint8_t tx_data[2] = {L3GD20H

Для сброса диалога введите команду /context
