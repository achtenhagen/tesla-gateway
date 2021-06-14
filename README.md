# Tesla Solar Gateway API ☀️
(Unofficial) API documentation currently supporting Tesla Gateway version `21.13.2` (0cf970371d2).

For basic instructions on how to monitor your Powerwall from home, visit Tesla's [website](https://www.tesla.com/support/energy/powerwall/own/monitoring-from-home-network).

### Base URL

- https://192.168.91.1
- https://teg
- https://teg-XXX (where XXX are the last 3 characters of the serial number)

### POST /api/login/Basic

Logs in the user.

Request Body:
```json
{
  "email": "YOUR_EMAIL",
  "password": "YOUR_PASSWORD",
  "username": "customer"
}
```

Response:
```json
{
  "email": "[REDACTED]",
  "firstname": "Tesla",
  "lastname": "Energy",
  "roles": [
    "Home_Owner"
  ],
  "token": "[REDACTED]",
  "provider": "Basic",
  "loginTime": "2021-05-22T10:59:54.126981306-04:00"
}
```

### POST /api/password/change

Updates the customer password.

Response:
```json
{
  "password": "[REDACTED]"
}
```

### GET /api/status

Returns the system status.

Response:
```json
{
  "start_time": "2021-05-19 14:43:51 +0800",
  "up_time_seconds": "53h7m8.673739945s",
  "is_new": false,
  "version": "21.13.2",
  "git_hash": "0cf970371d243fe78b08ab03774eb633720dd58a",
  "commission_count": 3,
  "device_type": "teg",
  "sync_type": "v2.1",
  "is_solar_powerwall": false
}
```

### GET /api/auth/toggle/supported

Response:
```json
{
  "toggle_auth_supported": true
}
```
### GET /api/site_info/site_name

Returns a summary of the site.

Response:
```json
{
  "site_name": "[REDACTED]",
  "timezone": "America/New_York"
}
```

### GET /api/site_info

Returns information about the site.

Response:
```json
{
  "measured_frequency": 59.980000000000004,
  "max_system_energy_kWh": 0,
  "max_system_power_kW": 0,
  "site_name": "[REDACTED]",
  "timezone": "America/New_York",
  "max_site_meter_power_kW": 1000000000,
  "min_site_meter_power_kW": -1000000000,
  "nominal_system_energy_kWh": 40.5,
  "nominal_system_power_kW": 15,
  "grid_code": {
    "grid_code": "60Hz_240V_s_IEEE1547a_2014",
    "grid_voltage_setting": 240,
    "grid_freq_setting": 60,
    "grid_phase_setting": "Split",
    "country": "United States",
    "state": "[REDACTED]",
    "distributor": "*",
    "utility": "[REDACTED]",
    "retailer": "*",
    "region": "IEEE1547a:2014"
  }
}
```

### GET /api/meters/aggregates

Returns information about the site, battery, load and solar.

Response:
```json
{
  "site": {
    "last_communication_time": "2021-05-21T16:51:00.090823193-07:00",
    "instant_power": 5,
    "instant_reactive_power": 156,
    "instant_apparent_power": 156.08010763707205,
    "frequency": 0,
    "energy_exported": 258.6174922525206,
    "energy_imported": 121713.57874840172,
    "instant_average_voltage": 208.2791096101575,
    "instant_total_current": 13.498000000000001,
    "i_a_current": 0,
    "i_b_current": 0,
    "i_c_current": 0,
    "last_phase_voltage_communication_time": "0001-01-01T00:00:00Z",
    "last_phase_power_communication_time": "0001-01-01T00:00:00Z",
    "timeout": 1500000000
  },
  "battery": {
    "last_communication_time": "2021-05-21T16:51:00.090472962-07:00",
    "instant_power": 1360,
    "instant_reactive_power": -20,
    "instant_apparent_power": 1360.1470508735442,
    "frequency": 60.004000000000005,
    "energy_exported": 24200,
    "energy_imported": 53100,
    "instant_average_voltage": 240.93333333333337,
    "instant_total_current": -29.400000000000002,
    "i_a_current": 0,
    "i_b_current": 0,
    "i_c_current": 0,
    "last_phase_voltage_communication_time": "0001-01-01T00:00:00Z",
    "last_phase_power_communication_time": "0001-01-01T00:00:00Z",
    "timeout": 1500000000
  },
  "load": {
    "last_communication_time": "2021-05-21T16:51:00.090306596-07:00",
    "instant_power": 1365.75,
    "instant_reactive_power": 118.5,
    "instant_apparent_power": 1370.8812175020855,
    "frequency": 0,
    "energy_exported": 0,
    "energy_imported": 146338.0214027785,
    "instant_average_voltage": 208.2791096101575,
    "instant_total_current": 6.557306695598598,
    "i_a_current": 0,
    "i_b_current": 0,
    "i_c_current": 0,
    "last_phase_voltage_communication_time": "0001-01-01T00:00:00Z",
    "last_phase_power_communication_time": "0001-01-01T00:00:00Z",
    "timeout": 1500000000
  },
  "solar": {
    "last_communication_time": "2021-05-21T16:51:00.090306596-07:00",
    "instant_power": 0,
    "instant_reactive_power": 0,
    "instant_apparent_power": 0,
    "frequency": 0,
    "energy_exported": 53797.48530917277,
    "energy_imported": 14.425162543468105,
    "instant_average_voltage": 208.03662249709785,
    "instant_total_current": 0.003,
    "i_a_current": 0,
    "i_b_current": 0,
    "i_c_current": 0,
    "last_phase_voltage_communication_time": "0001-01-01T00:00:00Z",
    "last_phase_power_communication_time": "0001-01-01T00:00:00Z",
    "timeout": 1500000000
  }
}
```
### GET /api/system_status/soe

Returns the Powerwall state of energy (SoE).

Response:
```json
{
  "percentage": 87.18218782148631
}
```

### GET /api/system_status/grid_status

Returns the status of the grid.

Response:
```json
{
  "grid_status": "SystemGridConnected",
  "grid_services_active": false
}
```
### GET /api/sitemaster

Response:
```json
{
  "status": "StatusUp",
  "running": true,
  "connected_to_tesla": true,
  "power_supply_mode": false,
  "can_reboot": "Yes"
}
```
### GET /api/customer/registration

Response:
```json
{
  "privacy_notice": true,
  "limited_warranty": true,
  "grid_services": true,
  "marketing": true,
  "registered": true,
  "timed_out_registration": false
}
```
### GET /api/system_status/grid_faults

Response:
```json
[
  {
    "timestamp": 1623278146367,
    "alert_name": "PINV_a007_vfCheckOverFrequency",
    "alert_is_fault": false,
    "decoded_alert": "[{\"name\":\"PINV_alertID\",\"value\":\"PINV_a007_vfCheckOverFrequency\"},{\"name\":\"PINV_alertType\",\"value\":\"Warning\"},{\"name\":\"PINV_a007_frequency\",\"value\":60.937,\"units\":\"Hz\"}]",
    "alert_raw": 504624507995029504,
    "git_hash": "0cf970371d243f",
    "site_uid": "[REDACTED]",
    "ecu_type": "TEPINV",
    "ecu_package_part_number": "[REDACTED]",
    "ecu_package_serial_number": "[REDACTED]"
  }
]
```
### GET /api/powerwalls

Returns detailed information about each Powerwall.

Response:
```json
{
  "enumerating": false,
  "updating": false,
  "checking_if_offgrid": false,
  "is_on_grid": true,
  "running_phase_detection": false,
  "phase_detection_last_error": "no phase information",
  "bubble_shedding": false,
  "on_grid_check_error": "",
  "grid_qualifying": false,
  "grid_code_validating": false,
  "phase_detection_not_available": true,
  "powerwalls": [
    {
      "Type": "",
      "PackagePartNumber": "[REDACTED]",
      "PackageSerialNumber": "[REDACTED]",
      "type": "ACPW",
      "grid_state": "Grid_Uncompliant",
      "grid_reconnection_time_seconds": 0,
      "under_phase_detection": false,
      "updating": false,
      "commissioning_diagnostic": {
        "name": "Commissioning",
        "category": "InternalComms",
        "disruptive": false,
        "inputs": null,
        "checks": [
          {
            "name": "CAN connectivity",
            "status": "fail",
            "start_time": "2021-06-13T18:32:28.282272677-04:00",
            "end_time": "2021-06-13T18:32:28.282280302-04:00",
            "message": "Cannot perform this action with site controller running. From landing page, either \"STOP SYSTEM\" or \"RUN WIZARD\" to proceed.",
            "results": {},
            "debug": {}
          },
          {
            "name": "Enable switch",
            "status": "fail",
            "start_time": "2021-06-13T18:32:28.282285927-04:00",
            "end_time": "2021-06-13T18:32:28.282290802-04:00",
            "message": "Cannot perform this action with site controller running. From landing page, either \"STOP SYSTEM\" or \"RUN WIZARD\" to proceed.",
            "results": {},
            "debug": {}
          },
          {
            "name": "Internal communications",
            "status": "fail",
            "start_time": "2021-06-13T18:32:28.282295676-04:00",
            "end_time": "2021-06-13T18:32:28.282300426-04:00",
            "message": "Cannot perform this action with site controller running. From landing page, either \"STOP SYSTEM\" or \"RUN WIZARD\" to proceed.",
            "results": {},
            "debug": {}
          },
          {
            "name": "Firmware up-to-date",
            "status": "fail",
            "start_time": "2021-06-13T18:32:28.282471667-04:00",
            "end_time": "2021-06-13T18:32:28.282477417-04:00",
            "message": "Cannot perform this action with site controller running. From landing page, either \"STOP SYSTEM\" or \"RUN WIZARD\" to proceed.",
            "results": {},
            "debug": {}
          }
        ]
      },
      "update_diagnostic": {
        "name": "Firmware Update",
        "category": "InternalComms",
        "disruptive": true,
        "inputs": null,
        "checks": [
          {
            "name": "Powerwall firmware",
            "status": "not_run",
            "start_time": null,
            "end_time": null,
            "progress": 0,
            "results": null,
            "debug": null
          },
          {
            "name": "Battery firmware",
            "status": "not_run",
            "start_time": null,
            "end_time": null,
            "progress": 0,
            "results": null,
            "debug": null
          },
          {
            "name": "Inverter firmware",
            "status": "not_run",
            "start_time": null,
            "end_time": null,
            "progress": 0,
            "results": null,
            "debug": null
          },
          {
            "name": "Grid code",
            "status": "not_run",
            "start_time": null,
            "end_time": null,
            "progress": 0,
            "results": null,
            "debug": null
          }
        ]
      },
      "bc_type": null,
      "in_config": true
    }
  ],
  "gateway_din": "[REDACTED]",
  "sync": {
    "updating": false,
    "commissioning_diagnostic": {
      "name": "Commissioning",
      "category": "InternalComms",
      "disruptive": false,
      "inputs": null,
      "checks": [
        {
          "name": "CAN connectivity",
          "status": "fail",
          "start_time": "2021-06-13T18:32:28.334712068-04:00",
          "end_time": "2021-06-13T18:32:28.335083674-04:00",
          "message": "Cannot perform this action with site controller running. From landing page, either \"STOP SYSTEM\" or \"RUN WIZARD\" to proceed.",
          "results": {},
          "debug": {}
        },
        {
          "name": "Firmware up-to-date",
          "status": "fail",
          "start_time": "2021-06-13T18:32:28.335094423-04:00",
          "end_time": "2021-06-13T18:32:28.335292913-04:00",
          "message": "Cannot perform this action with site controller running. From landing page, either \"STOP SYSTEM\" or \"RUN WIZARD\" to proceed.",
          "results": {},
          "debug": {}
        }
      ]
    },
    "update_diagnostic": {
      "name": "Firmware Update",
      "category": "InternalComms",
      "disruptive": true,
      "inputs": null,
      "checks": [
        {
          "name": "Synchronizer firmware",
          "status": "pass",
          "start_time": "2021-05-20T10:41:45.285678438-04:00",
          "end_time": "2021-05-20T10:41:45.384295582-04:00",
          "progress": 1,
          "results": {},
          "debug": {}
        },
        {
          "name": "Islanding configuration",
          "status": "pass",
          "start_time": "2021-05-20T10:41:45.384302331-04:00",
          "end_time": "2021-05-20T10:41:45.387224555-04:00",
          "progress": 1,
          "results": {},
          "debug": {}
        },
        {
          "name": "Grid code",
          "status": "pass",
          "start_time": "2021-05-20T10:41:45.38723143-04:00",
          "end_time": "2021-05-20T10:41:45.623503446-04:00",
          "progress": 1,
          "results": {},
          "debug": {}
        }
      ]
    }
  },
  "msa": null,
  "states": [
    "updating meter socket adapter"
  ]
}
```
