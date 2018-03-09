# prototype
a sample xcode project showing an issue with passed parameters and branch.io.  

In this example, when clicking this link on an iOS 10.3 device from a mobile browser (safari, for example)
```
https://ame9.app.link/ZaQRk2DB8K?username=redshedt&password=Shedred6!&officecode=redshed
```
the parameters **ARE NOT** passed to the branch deep link handler.  Here is the log output from branch:
```
2018-03-08 23:07:25.698134-0700 prototype[297:21439] [branch.io] BNCServerInterface.m(711) Debug: URL: https://api.branch.io/v1/open.
2018-03-08 23:07:25.698240-0700 prototype[297:21439] [branch.io] BNCServerInterface.m(715) Debug: Body: {
    "ad_tracking_enabled" = 1;
    "app_version" = "1.0";
    "apple_ad_attribution_checked" = 0;
    "branch_key" = "key_live_niuT29eJk70GFJtP7a4vhociyDpzT1zn";
    brand = Apple;
    cd =     {
        mv = "-1";
        pn = "com.redshedtechnology.prototype";
    };
    country = US;
    debug = 1;
    "device_fingerprint_id" = 500535028129039547;
    "facebook_app_link_checked" = 0;
    "hardware_id" = "C79E268F-2011-4E92-B62B-B757DB757E57";
    "hardware_id_type" = random;
    "identity_id" = 500535028166534048;
    instrumentation =     {
        "/v1/open-brtt" = 211;
    };
    "ios_bundle_id" = "com.redshedtechnology.prototype";
    "ios_vendor_id" = "790C3FE5-4F76-4741-8725-50D45A3F72F2";
    "is_hardware_id_real" = 0;
    language = en;
    "local_ip" = "192.168.1.196";
    model = "iPhone6,1";
    os = iOS;
    "os_version" = "10.3.3";
    retryNumber = 0;
    "screen_height" = 1136;
    "screen_width" = 640;
    sdk = "ios0.22.5";
    "universal_link_url" = "https://ame9.app.link/ZaQRk2DB8K?username=redshedt&password=Shedred6!&officecode=redshed";
    update = 1;
    "uri_scheme" = prototype;
    "user_agent" = "Mozilla/5.0 (iPhone; CPU iPhone OS 10_3_3 like Mac OS X) AppleWebKit/603.3.8 (KHTML, like Gecko) Mobile/14G60";
}
JSON: {"sdk":"ios0.22.5","facebook_app_link_checked":false,"language":"en","user_agent":"Mozilla/5.0 (iPhone; CPU iPhone OS 10_3_3 like Mac OS X) AppleWebKit/603.3.8 (KHTML, like Gecko) Mobile/14G60","screen_height":1136,"country":"US","app_version":"1.0","update":1,"universal_link_url":"https://ame9.app.link/ZaQRk2DB8K?username=redshedt&password=Shedred6!&officecode=redshed","brand":"Apple","ad_tracking_enabled":true,"retryNumber":0,"uri_scheme":"prototype","identity_id":"500535028166534048","os":"iOS","local_ip":"192.168.1.196","hardware_id":"C79E268F-2011-4E92-B62B-B757DB757E57","screen_width":640,"cd":{"pn":"com.redshedtechnology.prototype","mv":"-1"},"ios_vendor_id":"790C3FE5-4F76-4741-8725-50D45A3F72F2","ios_bundle_id":"com.redshedtechnology.prototype","hardware_id_type":"random","instrumentation":{"/v1/open-brtt":"211"},"debug":true,"os_version":"10.3.3","is_hardware_id_real":false,"model":"iPhone6,1","branch_key":"key_live_niuT29eJk70GFJtP7a4vhociyDpzT1zn","device_fingerprint_id":"500535028129039547","apple_ad_attribution_checked":false}.
2018-03-08 23:07:25.711222-0700 prototype[297:21439] [branch.io] BNCNetworkService.m(223) Debug: Network start operation https://api.branch.io/v1/open.
2018-03-08 23:07:28.803465-0700 prototype[297:21294] [branch.io] BNCNetworkService.m(219) Debug: Network finish operation https://api.branch.io/v1/open 3.106s. Status 200 error (null).
{"session_id":"500537414708974562","identity_id":"500535028166534048","link":"https://ame9.app.link?%24identity_id=500535028166534048","data":"{\"+clicked_branch_link\":false,\"+is_first_session\":false}","device_fingerprint_id":"500535028129039547"}.
2018-03-08 23:07:28.803923-0700 prototype[297:21438] [branch.io] BNCServerInterface.m(771) Debug: Server returned: Status: 200; Data: {
    data = "{\"+clicked_branch_link\":false,\"+is_first_session\":false}";
    "device_fingerprint_id" = 500535028129039547;
    "identity_id" = 500535028166534048;
    link = "https://ame9.app.link?%24identity_id=500535028166534048";
    "session_id" = 500537414708974562;
}.
2018-03-08 23:07:28.853731-0700 prototype[297:19150] params: {
    "+clicked_branch_link" = 0;
    "+is_first_session" = 0;
}
```
However, if you click this link a mobile browser
```
https://ame9.app.link/ZaQRk2DB8K?param1=my_name&param2=my_pw&param3=my_code
```
The parameters **ARE** passed to the deeplink handler:
```
2018-03-08 23:10:53.791171-0700 prototype[297:22124] [branch.io] BNCServerInterface.m(715) Debug: Body: {
    "ad_tracking_enabled" = 1;
    "app_version" = "1.0";
    "apple_ad_attribution_checked" = 0;
    "branch_key" = "key_live_niuT29eJk70GFJtP7a4vhociyDpzT1zn";
    brand = Apple;
    cd =     {
        mv = "-1";
        pn = "com.redshedtechnology.prototype";
    };
    country = US;
    debug = 1;
    "device_fingerprint_id" = 500535028129039547;
    "facebook_app_link_checked" = 0;
    "hardware_id" = "C79E268F-2011-4E92-B62B-B757DB757E57";
    "hardware_id_type" = random;
    "identity_id" = 500535028166534048;
    instrumentation =     {
        "/v1/close-brtt" = 469;
    };
    "ios_bundle_id" = "com.redshedtechnology.prototype";
    "ios_vendor_id" = "790C3FE5-4F76-4741-8725-50D45A3F72F2";
    "is_hardware_id_real" = 0;
    language = en;
    "local_ip" = "192.168.1.196";
    model = "iPhone6,1";
    os = iOS;
    "os_version" = "10.3.3";
    retryNumber = 0;
    "screen_height" = 1136;
    "screen_width" = 640;
    sdk = "ios0.22.5";
    "universal_link_url" = "https://ame9.app.link/ZaQRk2DB8K?param1=my_name&param2=my_pw&param3=my_code";
    update = 1;
    "uri_scheme" = prototype;
    "user_agent" = "Mozilla/5.0 (iPhone; CPU iPhone OS 10_3_3 like Mac OS X) AppleWebKit/603.3.8 (KHTML, like Gecko) Mobile/14G60";
}
JSON: {"sdk":"ios0.22.5","facebook_app_link_checked":false,"language":"en","user_agent":"Mozilla/5.0 (iPhone; CPU iPhone OS 10_3_3 like Mac OS X) AppleWebKit/603.3.8 (KHTML, like Gecko) Mobile/14G60","screen_height":1136,"country":"US","app_version":"1.0","update":1,"universal_link_url":"https://ame9.app.link/ZaQRk2DB8K?param1=my_name&param2=my_pw&param3=my_code","brand":"Apple","ad_tracking_enabled":true,"retryNumber":0,"uri_scheme":"prototype","identity_id":"500535028166534048","os":"iOS","local_ip":"192.168.1.196","hardware_id":"C79E268F-2011-4E92-B62B-B757DB757E57","screen_width":640,"cd":{"pn":"com.redshedtechnology.prototype","mv":"-1"},"ios_vendor_id":"790C3FE5-4F76-4741-8725-50D45A3F72F2","ios_bundle_id":"com.redshedtechnology.prototype","hardware_id_type":"random","instrumentation":{"/v1/close-brtt":"469"},"debug":true,"os_version":"10.3.3","is_hardware_id_real":false,"model":"iPhone6,1","branch_key":"key_live_niuT29eJk70GFJtP7a4vhociyDpzT1zn","device_fingerprint_id":"500535028129039547","apple_ad_attribution_checked":false}.
2018-03-08 23:10:53.810549-0700 prototype[297:22124] [branch.io] BNCNetworkService.m(223) Debug: Network start operation https://api.branch.io/v1/open.
2018-03-08 23:10:53.962178-0700 prototype[297:22095] [branch.io] BNCNetworkService.m(219) Debug: Network finish operation https://api.branch.io/v1/open 0.171s. Status 200 error (null).
{"session_id":"500538287535313819","identity_id":"500535028166534048","link":"https://ame9.app.link?%24identity_id=500535028166534048","data":"{\"$marketing_title\":\"Prototype Link\",\"~creation_source\":1,\"+click_timestamp\":1520575853,\"param3\":\"my_code\",\"~feature\":\"marketing\",\"param1\":\"my_name\",\"param2\":\"my_pw\",\"+match_guaranteed\":true,\"~marketing\":true,\"+clicked_branch_link\":true,\"$one_time_use\":false,\"~id\":500532302431127075,\"+is_first_session\":false,\"~referring_link\":\"https://ame9.app.link/ZaQRk2DB8K?param1=my_name&param2=my_pw&param3=my_code\"}","device_fingerprint_id":"500535028129039547"}.
2018-03-08 23:10:53.962551-0700 prototype[297:22095] [branch.io] BNCServerInterface.m(771) Debug: Server returned: Status: 200; Data: {
    data = "{\"$marketing_title\":\"Prototype Link\",\"~creation_source\":1,\"+click_timestamp\":1520575853,\"param3\":\"my_code\",\"~feature\":\"marketing\",\"param1\":\"my_name\",\"param2\":\"my_pw\",\"+match_guaranteed\":true,\"~marketing\":true,\"+clicked_branch_link\":true,\"$one_time_use\":false,\"~id\":500532302431127075,\"+is_first_session\":false,\"~referring_link\":\"https://ame9.app.link/ZaQRk2DB8K?param1=my_name&param2=my_pw&param3=my_code\"}";
    "device_fingerprint_id" = 500535028129039547;
    "identity_id" = 500535028166534048;
    link = "https://ame9.app.link?%24identity_id=500535028166534048";
    "session_id" = 500538287535313819;
}.
2018-03-08 23:10:53.995102-0700 prototype[297:19150] params: {
    "$marketing_title" = "Prototype Link";
    "$one_time_use" = 0;
    "+click_timestamp" = 1520575853;
    "+clicked_branch_link" = 1;
    "+is_first_session" = 0;
    "+match_guaranteed" = 1;
    param1 = "my_name";
    param2 = "my_pw";
    param3 = "my_code";
    "~creation_source" = 1;
    "~feature" = marketing;
    "~id" = 500532302431127075;
    "~marketing" = 1;
    "~referring_link" = "https://ame9.app.link/ZaQRk2DB8K?param1=my_name&param2=my_pw&param3=my_code";
}
```
