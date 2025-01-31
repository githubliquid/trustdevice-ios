<p align="center">
  <a href="https://www.trustdecision.com/deviceFingerprint" >
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="images/logo_light.png" />
      <source media="(prefers-color-scheme: light)" srcset="images/logo_dark.png" />
      <img src="images/logo_dark.png" alt="trustdevice logo" width="729px" height="67px"/>    </picture>
  </a>
</p>

<p align="center">
  <img src="images/demoApp.gif" width="195">
</p>


# TrustDevice-iOS
A lightweight library for determining device uniqueness and risk identification.

Create a device identifier based on basic device information.

Will remain the same after uninstalling and reinstalling or clearing app data.

## Quick Start 

### 1. Add Dependcy

TrustDecision is available through [CocoaPods](https://cocoapods.org). To install it, simply add the following line to your Podfile:

```ruby
# Podfile
pod 'TrustDecision', '1.0'
```

### 2. Get DeviceInfo
DeviceInfo contains device id, risk information and device details.

#### Objective-C

```objective-c
#import <TrustDecision/TongdunMobRisk.h>

TongdunMobRiskManager_t *manager = [TongdunMobRiskManager sharedManager];
NSMutableDictionary *options = [[NSMutableDictionary alloc] init];
[options setObject:^(NSDictionary *response) {
    // Response in sub-thread, do something with the response
    // Get DeviceId
    NSString *deviceId = response[@"device_id"];
    // Get DeviceRiskLabel
    NSDictionary *deviceRisk = response[@"device_risk_label"];
    // Get DeviceDetail
    NSDictionary *deviceDetail = response[@"device_detail"];
} forKey:@"callback"];
manager->initWithOptions(options);
```

#### Swift

```swift
import TrustDecision

var options = [String : NSObject]()
let responseCallback: ([String : Any])-> Void = { response in
    // Response in sub-thread, do something with the response
    // Get DeviceId
    let deviceId = response["device_id"]   
    // Get DeviceRiskLabel
    let deviceRisk = response["device_risk_label"]
    // Get DeviceDetail
    let deviceDetail = response["device_detail"]                                         
}
options["callback"] = unsafeBitCast(responseCallback as @convention(block) ([String : Any]) -> Void, to: AnyObject.self) as? NSObject
let manager = TongdunMobRiskManager.sharedManager()
manager?.pointee.initWithOptions(options)
```

## Data Sample
```json
{
    "device_id":"95438cde98fc3f18b9ffb7d464ec7abbd8225efa7b6199aee552d7563a5d4f0e",
    "device_risk_label":{
        "debug":true,
        "jailbreak":false,
        "simulator":false
    },
    "device_detail":{
        "appVersion":"1.0",
        "bootTime":1670888977003957,
        "bundleId":"org.cocoapods.demo.TrustDecision-Example",
        "cpuCount":"6",
        "currentTime":1670983993560205,
        "debug":true,
        "deviceModel":"N104AP",
        "deviceType":"iPhone",
        "displayResolution":"828.0x1792.0",
        "displayScale":2,
        "freeDiskSpace":4624658432,
        "idfv":"52FBDFEB-EBA3-4819-A92D-C456A2DE8FE0",
        "jailbreak":false,
        "kernelVersion":"Darwin Kernel Version 22.0.0: Tue Aug 16 20:50:57 PDT 2022; root:xnu-8792.2.11.0.1~1\/RELEASE_ARM64_T8030",
        "memorySize":"4038836224",
        "osRelease":"22.0.0",
        "osType":"Darwin",
        "osVersion":"20A362",
        "physicalMemory":"8333803520",
        "simulator":false,
        "totalDiskSpace":127933894656
    }
}
```
## Open Source Features

+ Basic device ID, consistent when uninstalling applications and reinstalling
+ Basic equipment information, which can be used for simple data analysis
+ Basic risk identification ability

| RiskLabel      |       Risk Description |
| --------- | --------------------------- |
| jailbreak   |     Attackers will have higher privileges and can install many cheating software to affect the normal development of application business.      |
| simulator   | The simulator provides many simulation functions, which will affect the normal operation of applications, such as virtual positioning. |
| debug   |   Applications can be modified by attackers at will, and the program will return unexpected values.         |


## Open Source VS Pro
| Ability | Open Source |  Pro  |
| :-------: | :-------: | :-------------------------: |
| 100% open source | Yes | No |
| Device ID | Basic | Extremely stable, even if the device is restored to factory settings, it can still be recognized as the same |
| Device Risk Label | Basic | Extremely rich |
| Device Details | Basic  | Extremely rich |
| IP Location | -  | ✓ |
| Device Risk Score | -  | ✓ |
| Environment Risk Evaluation | -  | ✓ |
| Fraud Tools Detection | -  | ✓ |
| Behavioral Activity Capturing | -  | ✓ |

## Pro Introduction

TrustDecision TrustDevice has the leading device fingerprint technology, which has been integrated by more than 10000 global leading brands, protecting the entire customer journey.

**There are 6 leading core features about TrustDevice Pro:**

### 1. Wide Coverage
Comprehensive coverage of Android, iOS, Web, H5, applets and other device types.

### 2. Stable and Reliable
TrustDevice served more than 10,000 clients, 200 million+ daily active users , and 6 billion+ devices , with excellent product functions and stability.
The fingerprint accuracy of different terminal devices exceeded 99.9%, and the output of risk labels exceeded 70 items.

### 3. Unparalleled Safety
TrustDevice's code virtualization & obfuscation technology make the malware fraudsters suffer from painful cost and imprecision when performing reverse-engineering.

### 4. Core Intellectual Property
Fully independent intellectual property rights, with a number of patented technology.

### 5. Security Compliance
TrustDevice is committed to the highest standards in security and compliance to keep your data safe.
GDPR/CCA/PCI DSS/ISO 27701/ISO 9001 Compliant.

### 6. Easy to Deploy
SaaS（Software as a Service）deployment supported, reducing massively your integration cost and enabling rapid access to device fingerprint service.

## Where to get support
We are happy to provide technical support for our open-source trustdevice-ios library. We recommend using GitHub Issues to submit bugs or Discussions to ask questions. Using [Issues](https://github.com/trustdecision/trustdevice-ios/issues) and [Discussions](https://github.com/trustdecision/trustdevice-ios/discussions) publicly will help the open-source community and other users with similar issues.

In addition, any idea or interest in using TrustDevice Pro can be found on the [www.trustdecision.com](https://www.trustdecision.com/trustDevice), registered account for a free trial; or via email trustdevice@trustdecision.com contact us directly and quickly open the service.

## Compatibility
| Items     | Description          |
| :-------: | :-------------------------: |
| Supported System Versions | iOS9.0+              |
| Supported Architecture   | armv7, arm64, x86_64 |

## License

This library is MIT licensed. Copyright trustdecision, Inc. 2022.
