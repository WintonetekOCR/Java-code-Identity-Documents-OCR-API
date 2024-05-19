# Java Code Identity Documents OCR API 

## Introduction
The document OCR recognition service can quickly and accurately recognize ID cards, passports, driving licenses, car licenses and other identity documents and provides an OCR API interface, OCR rreading result can be called by Java language, below is the sample source code for your reference. 

## Java Source Code 
```package com.test;

import okhttp3.*;
import org.json.JSONObject;
import java.io.*;
/**
 * 需要添加依赖
 * 
 * 
 *     com.squareup.okhttp3
 *     okhttp
 *     4.12.0
 * 
 */
class Sample {

	static final OkHttpClient HTTP_CLIENT = new OkHttpClient().newBuilder().build();

	public static void main(String []args) throws IOException{
		MediaType mediaType = MediaType.parse("text/plain");
		RequestBody body = new MultipartBody.Builder().setType(MultipartBody.FORM)
		  .addFormDataPart("img","/9j")
		  .addFormDataPart("key","M***********g")
		  .addFormDataPart("secret","3***********6")
		  .addFormDataPart("typeId","2")
		  .addFormDataPart("format","json")
		  .build();
		Request request = new Request.Builder()
		  .url("https://netocr.com/api/recogliu.do")
		  .method("POST", body)
		  .build();
		Response response = HTTP_CLIENT.newCall(request).execute();
		System.out.println(response.body().string());
	}
}
```


