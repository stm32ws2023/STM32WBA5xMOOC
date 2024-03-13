----!
Presentation
----!



# Add application code to move to discoverable
<br>

> CubeMX/STM32CubeIDE .IOC project for the HandsOn1 can be downloaded from [here](https://github.com/stm32ws2023/WBA_WS_ioc/blob/main/Hands-On_WS_WBA52.ioc)
<br>

1.code needs to be added in **STM32_WPAN/App/app_ble.c** inside the function App_BLE_Init() Search for **/*USER CODE BEGIN APP_BLE_Init_2*/**

```c
  /* USER CODE BEGIN APP_BLE_Init_2 */
  tBleStatus status;
  status = aci_gap_set_discoverable(ADV_TYPE, ADV_INTERVAL_MIN,ADV_INTERVAL_MAX,
                                             CFG_BD_ADDRESS_TYPE,
                                             ADV_FILTER,
                                             0, 0, 0, 0, 0, 0);
  if (status != BLE_STATUS_SUCCESS) {
	  return;
  }

  status = aci_gap_delete_ad_type(AD_TYPE_TX_POWER_LEVEL);
  if (status != BLE_STATUS_SUCCESS) {
	  return;
  }

  status = aci_gap_update_adv_data(sizeof(a_AdvData), (uint8_t*) a_AdvData);
  if (status != BLE_STATUS_SUCCESS) {
	  return;
  }
  /* USER CODE END APP_BLE_Init_2 */
```
2.still in **STM32_WPAN/App/app_ble.c** inside SVCCTL_App_Notification function Search for **/*USER CODE BEGIN EVT_DISCONN_COMPLETE*/**

```c
      /* USER CODE BEGIN EVT_DISCONN_COMPLETE */
  tBleStatus status;
  status = aci_gap_set_discoverable(ADV_TYPE, ADV_INTERVAL_MIN,ADV_INTERVAL_MAX,
                                             CFG_BD_ADDRESS_TYPE,
                                             ADV_FILTER,
                                             0, 0, 0, 0, 0, 0);
  if (status != BLE_STATUS_SUCCESS) {
	  LOG_INFO_APP("==>> aci_gap_set_discoverable - fail, result: 0x%02X\n", status);
  }

  status = aci_gap_delete_ad_type(AD_TYPE_TX_POWER_LEVEL);
  if (status != BLE_STATUS_SUCCESS) {
	  LOG_INFO_APP("==>> delete tx power level - fail, result: 0x%02X\n", status);
  }

  status = aci_gap_update_adv_data(sizeof(a_AdvData), (uint8_t*) a_AdvData);
  if (status != BLE_STATUS_SUCCESS) {
	   LOG_INFO_APP("==>> Start Advertising Failed, result: 0x%02X\n", status);
  }
     /* USER CODE END EVT_DISCONN_COMPLETE */
```




