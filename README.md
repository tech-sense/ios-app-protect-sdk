# SenseOSProtect - iOS SDK 

Sense is a device intelligence and identification tool. This tool collects a comprehensive set of attributes unique to a device or browser, forming an identity that will help businesses.

## Requirements
    * iOS 12.0 or above
    * Swift version 5.0 and above

### Step 1 - Installation
```
pod 'SenseOSProtect', '~> 0.0.1'
pod update
```
### Step 2 - Import SDK
```
import SenseOSProtect
```


#### Installed Applications Information

If you need installed applications using this SDK, you have to add the code below.

```
let localPackageList: [(packageName: String, packageCode: String)] = [
                    (“Package Name”, “Package Code”)]        
        let config = SenseOSProtectConfig(installedAppList: localPackageList)
```

To initialize the SDK add the below line of code.

```
    func initiateSense(){
        let config = SenseOSProtectConfig(installedAppList: localPackageList)
        SenseOSProtect.initSDK(senseConfig: config, withDelegate: self)
        SenseOSProtect.getSenseDetails(withDelegate: self)
    }

```

If you pass allowGeoLocation as true in above config means, it will return Device Location Information in Sense Details via our Server API.


### Step 3 - Implement  Delegate Method
Use the below code to obtain the Device result.
```
extension ViewController:  SenseOSProtectDelegate{
    func onFailure(message: String) {
        // Failure Callback.
    }
    func onSuccess(data: [String : Any]) {
        // Success Callback
    }
}
```
### Step 4 - Get Applcation Security Features
By call the following delegate to receive the Applcation Security Features shown below.
```
 SenseOSProtect.getSenseDetails(withDelegate: self)
```

### Step 5 - If you need to know Installed Applications in our SDK, kindly update your Info.plist like below. You can add those apps that you need to check whether it's installed or not.

```
<key>LSApplicationQueriesSchemes</key>
<array>
    <string>whatsapp</string>
    <string>tez</string>
    <string>phonepe</string>
    <string>cred</string>
    <string>amazon</string>
</array>

```