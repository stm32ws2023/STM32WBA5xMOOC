----!
Presentation
----!



# Add application code to move to discoverable
<br>

> CubeMX/STM32CubeIDE .IOC project for this MOOC can be downloaded from [here](https://github.com/stm32ws2023/STM32WBA5xMOOC/blob/main/MOOC_IOC/Hands-On_WS_WBA55.ioc)
<br>

1.code needs to be added in **STM32_WPAN/App/app_ble.c** inside the function App_BLE_Init() Search for **/*USER CODE BEGIN APP_BLE_Init_2*/**

```c
  /* USER CODE BEGIN APP_BLE_Init_2 */
  APP_BLE_Procedure_Gap_Peripheral(PROC_GAP_PERIPH_ADVERTISE_START_FAST);
  /* USER CODE END APP_BLE_Init_2 */
```
2.still in **STM32_WPAN/App/app_ble.c** inside SVCCTL_App_Notification function Search for **/*USER CODE BEGIN EVT_DISCONN_COMPLETE*/**

```c
      /* USER CODE BEGIN EVT_DISCONN_COMPLETE */
      APP_BLE_Procedure_Gap_Peripheral(PROC_GAP_PERIPH_ADVERTISE_START_FAST);
      /* USER CODE END EVT_DISCONN_COMPLETE */
```




