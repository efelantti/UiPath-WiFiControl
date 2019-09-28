# UiPath-WiFiControl
UiPath project for automated enabling and disabling home WiFi network. The project works with my Arris TG2492 modem.

## Details

### Process

1. Ask user whether should enable or disable WiFi.
2. Initialize hidden browser (user cannot interfere with the process).
2. Navigate to modem control page, login and enable / disable.
3. Close browser and throw exception (if caught).

### Architecture / Exception handling

Process is straightforward enough so it is just a sequence that is contained in a try-catch activity. The try-catch is configured
so that even though exceptions would be thrown, the browser object is any way closed.

#### Test workflows

All workflows have a corresponding test workflow that allows running them on-demand, which makes debugging much easier.

## What do I need to run it?
### 1. UiPath installed on system

Project created on 2019.8.0

### 2. UiPath Orchestrator account

Possible to create for free (with restrictions) via [UiPath Cloud platform](https://cloud.uipath.com/).

### 3. Orchestrator assets configured

Uses following assets:

| Asset  |  Description
|---|---
| WifiControl_ArrisControlPageUrl | Url to Arris control page (default 192.168.0.1).
| WifiControl_ArrisCredentials | Username and password to access Arris control page.
| WifiControl_EnableHighFrequencyNetwork | Boolean. If set to True, will enable 5 GHz WiFi network.
| WifiControl_EnableLowFrequencyNetwork | Boolean. If set to Fales, will enable 2.4 GHz WiFi network.
