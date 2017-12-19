# How to Debug React Native on iOS Device with Chrome Developer Tools

### Prerequisites:
- Make sure your project scheme is Debug build, not Release build.
- Make sure host macOS machine and iOS device joined the same network.

### Steps:
- Find out your host macOS machine's IP address (in System Preference).

- In Xcode, navigate to `RCTWebSocket.xcodeproj` of your Libraries, open [`RCTWebSocketExecutor.m`](https://github.com/facebook/react-native/blob/master/Libraries/WebSocket/RCTWebSocketExecutor.m#L58), in `- (void)setUp` method, replace `@"localhost"` with the host machine IP address.
```Objective-C
- (void)setUp
{
  if (!_url) {
    NSInteger port = [[[_bridge bundleURL] port] integerValue] ?: 8081;
    NSString *host = [[_bridge bundleURL] host] ?: @"localhost"; // Change @"localhost" to your machine's IP address
    NSString *URLString = [NSString stringWithFormat:@"http://%@:%lld/debugger-proxy?role=client", host, (long long)port];
    _url = [RCTConvert NSURL:URLString];
  }
  ...
}
```

- In terminal, execute the following command to generate the proper jsbundle file.
```
react-native bundle --dev false --assets-dest ./ios --entry-file index.ios.js --platform ios --bundle-output ios/main.jsbundle
```

- Build and Run project from Xcode.

---
Reference:
- [React Native documentation on debugging on a device](https://facebook.github.io/react-native/docs/debugging.html#debugging-on-a-device-with-chrome-developer-tools)
