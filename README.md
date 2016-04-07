# okhttp-basicparamsinterceptor

[![](https://jitpack.io/v/jkyeo/okhttp-basicparamsinterceptor.svg)](https://jitpack.io/#jkyeo/okhttp-basicparamsinterceptor)

A Basic Params Interceptor for okhttp3.

Via this interceptor we can inject header, url-query and even body (post with "x-www-form-urlencoded" contentType) params into every http request in okhttp3.

## Setup

__Step 1.__ Add the JitPack repository to your build file

Add it in your root build.gradle at the end of repositories:

```gradle
allprojects {
	repositories {
		...
		maven { url "https://jitpack.io" }
	}
}
```

__Step 2.__ Add the dependency

```gradle
dependencies {
        compile 'com.github.jkyeo:okhttp-basicparamsinterceptor:v0.9'
}
```

## Usage

```java
BasicParamsInterceptor basicParamsInterceptor =
        new OkPublicParamsInterceptor.Builder()
                .addHeaderParam("device_id", DeviceUtils.getDeviceId())
                .addParam("uid", UserModel.getInstance().getUid())
                .addQueryParam("api_version", "1.1")
                .build();


OkHttpClient client = new OkHttpClient.Builder()
        .addInterceptor(basicParamsInterceptor)
        .build();
