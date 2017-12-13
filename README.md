# Relaxful

Relaxful is a REST API client written in Obj-C.
Relaxful can be used on all Apple platforms, iOS,tvOS,watchOS, and macOS.  

## Use

### Simple Request

```obj-c
Relaxer *relaxer = [[Relaxer alloc] init];
[relaxer request:@"http://api.com" errorBlock:^(NSError * _Nonnull error) {
  // handle error
} completion:^(Response * _Nonnull response) {
  // handle response
  if(response.validate) {
    // response.text is the body of the API request
    NSLog(response.text);
  } else {
    // response is not valid
  }
}];
```

### Parameters

```obj-c

```

### Headers

```obj-c

```

### JSON Object

```obj-c
Relaxer *relaxer = [[Relaxer alloc] init];
[relaxer request:@"http://api.com" errorBlock:^(NSError * _Nonnull error) {
  // handle error
} completion:^(Response * _Nonnull response) {
  // handle response
  if(response.validate) {
   if(response.jsonObject != nil) {
    // parse json object
   }
  } else {
    // response is not valid
  }
}];
```

### JSON Array

```obj-c
Relaxer *relaxer = [[Relaxer alloc] init];
[relaxer request:@"http://api.com" errorBlock:^(NSError * _Nonnull error) {
  // handle error
} completion:^(Response * _Nonnull response) {
  // handle response
  if(response.validate) {
    if(response.jsonArray != nil) {
      // parse json array
    }
  } else {
    // response is not valid
  }
}];
```

### File Upload

File Upload without parameters.

```obj-c

```

File Upload with paramters.

```obj-c

```

## Build

If not using CocoaPods, build each target and navigate to its  
build directory to find the universal framework file.

Drag this into your project and check 'Copy items if needed'.  
Be sure to add your framework to the 'Embedded Binaries' of your project.  

Import into your project

```#import <Relaxful/Relaxer.h>```
