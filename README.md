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
NSDictionary *bodyDict = [NSMutableDictionary dictionary];

[bodyDict setValue:@"data" forKey:@"param1"];

[relaxer request:@"GET" url:@"http://url.com" body:bodyDict headers:nil errorBlock:^(NSError * _Nonnull error) {
   // handle error     
} completion:^(Response * _Nonnull response) {
   // handle response
}];
```

### Headers

```obj-c
NSDictionary *headersDict = [NSMutableDictionary dictionary];

[headersDict setValue:@"data" forKey:@"header1"];

[relaxer request:@"GET" url:@"http://url.com" body:nil headers:headersDict errorBlock:^(NSError * _Nonnull error) {
   // handle error     
} completion:^(Response * _Nonnull response) {
   // handle response
}];
```

### JSON Object

```obj-c
Relaxer *relaxer = [[Relaxer alloc] init];
[relaxer request:@"http://api.com" errorBlock:^(NSError * _Nonnull error) {
  // handle error
} completion:^(Response * _Nonnull response) {
  // handle response
  if(response.validate) {
   if(response.jsonObject) {
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
    if(response.jsonArray) {
      // parse json array
      
      NSError *error;
      NSDictionary *json = [NSJSONSerialization JSONObjectWithData:responseData options:kNilOptions error:&error];

      if(!error) {
         NSArray *fetchedArr = (NSArray *)json;

        for (NSArray *arr in fetchedArr) {
          // access values here
        }
      } else {
        // handle error
      }
    }
  } else {
    // response is not valid
  }
}];
```

### File Upload

To get progress and feedback on your file upload, be sure  
to implement the ```UploadDelegate``` Class.

The ```fileKey``` parameter is the name of the 'input' for the file,  
this is what the server is looking for in the upload.  

The ```fileName``` parameter is the readable name of the file.

The ```mime``` parameter is the file MIME type.

The ```fileData``` parameter is an ```NSData``` object representing the file.  

The ```body``` and ```headers``` parameter(s) are the same as in a regular API request. 

```obj-c
Relaxer *relaxer = [[Relaxer alloc] init];
 
[relaxer upload:@"POST" url:@"https://url.com" body:nil headers:nil fileKey:@"images" fileName:@"image.png" mime:@"png" fileData:data uploadDelegate:nil];
```

### File Upload Delegate

Be sure to include the delegate.  

```#import <Relaxful/UploadDelegate.h>```

```obj-c
// upload finished
- (void) uploadFinished:(Response *)response :(NSError *)error {
  // handle upload finished
  if(error) {
    // handle error
  } else {
    // success
}

// progress update
- (void) uploadProgress:(int64_t)bytesSent :(int64_t)totalBytesSent :(int64_t)totalBytesExpectedToSend {
  // handle progress
  int uploadProgress = totalBytesSent / totalBytesExpectedToSend;
    
  // set this on your UIProgressView
  int progressPercent = uploadProgress*100;
}

```

### Response

A response object contains properties and formatted data from
the API Call.

Note: all properties are optional except for 'status'.

Accessable Properties are:

- response, the URLResponse
- status, the HTTP Status
- text, the HTTP Body
- data, HTTP Body Data
- headers, the response headers

## Build

If not using CocoaPods, build each target and navigate to its  
build directory to find the universal framework file.

Drag this into your project and check 'Copy items if needed'.  
Be sure to add your framework to the 'Embedded Binaries' of your project.  

Import into your project

```#import <Relaxful/Relaxer.h>```
