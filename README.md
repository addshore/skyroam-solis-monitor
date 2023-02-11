# Skyroam solis monitor

I have been having some problems with my old Skyroam solis.

After looking in the JS of the landing page I found some endpoints that can be useful to see whats going on...

## The cgi-bin endpoints

```
$ curl http://192.168.43.1/assets/js/sys.js | grep cgi-bin
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0          url: url + "cgi-bin/get_netstat?callback=?",
                url: url + "cgi-bin/get_skyroam_service_error_string?callback=?",
                url: url + "cgi-bin/get_progress_bar?callback=?",
                url: url + "cgi-bin/get_service_url?callback=?",
                url: url + "cgi-bin/get_data_link_status?callback=?",
                url: url + "cgi-bin/get_battery_percent?callback=?",
                url: url + "cgi-bin/get_wifi_status?callback=?",
                url: url + "cgi-bin/get_dev_info?callback=?",
                url: url + "cgi-bin/net_reconnect?callback=?",
                url: url + "cgi-bin/system_reboot?callback=?",
                url: url + "cgi-bin/restore_factory_settings?callback=?",
                url: url + "cgi-bin/ota_upgrade?callback=?",
                url: url + "cgi-bin/get_onekey_dp_status?callback=?",
                url: url + "cgi-bin/set_onekey_dp_status?onekey_dp_status=" + onekey,
                url: url + "cgi-bin/get_hwsim_status?callback=?",
                url: url + "cgi-bin/set_hwsim_status?hwsim_status=" + onekey,
                url: url + "cgi-bin/get_bt_client?callback=?",
100 33050  100 33050    0     0  1793k      0 --:--:-- --:--:-- --:--:-- 1793k
```

## monitor.sh

Provides you all the raw info I found

```sh
$ ./monitor.sh 
get_battery_percent {"result":"92", "isCharge":"no"}
get_progress_bar {"result":"100"}
get_skyroam_service_error_string {"result":"network_broken"}
get_service_url {"result":"0","url":"https://bsp.skyroam.com/ehall", "suffix":""}
get_data_link_status {"result":"on"}
get_wifi_status {"result":"0", "ssid":"\#Skyroam_xxxx", "psk":"xxxx", "sta_num":"3"}
get_dev_info {"result":"0", "sn":"xxxx","skyroam_id":"xxxx","version":"9.1.5.4", "firmware":"2.13.14", "dp_actived":"1", "lefttime":"260:19"}
get_onekey_dp_status {"result":"enable"}
get_hwsim_status {"result":"0"}
```

## Do stuff

 - `net_reconnect.sh` ?
 - `system_reboot.sh`: Restarts the solis