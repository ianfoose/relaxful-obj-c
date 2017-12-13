# Relaxful

Relaxful is a REST API client written in Obj-C.
Relaxful can be used on all Apple platforms, iOS,tvOS,watchOS, and macOS.  

## Use

### Simple Request

```obj-c
Relaxer *relaxer = Relaxer();
[relaxer request:@"http://api.com"
errorBlock:(void (^_Nonnull)(NSError * _Nonnull error))errorBlock 
completion:(void (^_Nonnull)(Response* _Nonnull response))completion];

```

### JSON Object

```obj-c

```

### JSON Array

```obj-c

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
