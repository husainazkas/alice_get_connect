**AliceGetConnect** is a Flutter library that enables seamless integration 
between the HTTP Inspector library 
[alice](https://pub.dev/packages/alice),
and the HTTP Networking library get_connect from [GetX](https://pub.dev/packages/get).

This is forked repo from https://github.com/teknologicakrainternasional/alice_get_connect

## Features

- Detailed logs for each HTTP call (HTTP Request, HTTP Response)
- Inspector UI for viewing HTTP calls
- Statistics tracking
- Error handling capabilities
- HTTP call search functionality
- Bubble overlay entry support
- Support for GetConnect from GetX
- Handle connection timeout

## Usage

1. Create AliceGetConnect instance
```dart
AliceGetConnect alice = AliceGetConnect();
```
Since GetConnect does not have a callback for handling connection timeouts, AliceGetConnect will by default consider a request timeout if it exceeds 30 seconds. You can also set the timeout by configuring the time parameters at initialization
```dart
AliceGetConnect alice = AliceGetConnect(
  timeout: const Duration(seconds: 60)
);
```
You can also use it to set the timeout in getConnect
```dart
httpClient.timeout = alice.timeout;
```
2. Add navigator key to GetMaterialApp
```dart
GetMaterialApp(navigatorKey: alice.getNavigatorKey(), home: ...);
```
You need to add this navigator key in order to show inspector UI. You can use also your navigator key in Alice:
```dart
AliceGetConnect(navigatorKey: _navKey);
```
3. Add Request & Response Modifier
```dart
httpClient.addRequestModifier(alice.requestInterceptor);
httpClient.addResponseModifier(alice.responseInterceptor);
```