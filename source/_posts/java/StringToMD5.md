---
title: Java 字符串转 MD5方法
p: ./java
date: 2016-05-18 00:33:21
tags:
  - java
category: android
---




``` java

import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;

public class Md5test {

	public static void main(String[] args) {
		MessageDigest md = null;
		try {
			md = MessageDigest.getInstance("MD5");
		} catch (NoSuchAlgorithmException e) {
			e.printStackTrace();
		}
		String input = "you password";
		//字符串转byte数组
		byte[]in=input.getBytes();
		md.update(in);
		byte []sum=md.digest();
		String out="";
		//使用增强for循环将byte字符数组拼接成字符串
		//:X表示以十六进制形式输出02表示不足两位,前面补0输出
		for(byte o:sum){
			out=out+String.format("%02X",o);
		}
		System.out.println(out);

	}

}

```

**得到结果如下：68289CE0D4A89F292F11626DCE295CD3**

> 此 MessageDigest 类为应用程序提供信息摘要算法的功能，如 MD5 或 SHA 算法。信息摘要是安全的单向哈希函数，它接收任意大小的数据，并输出固定长度的哈希值。
MessageDigest 对象开始被初始化。该对象通过使用 update 方法处理数据。任何时候都可以调用 reset 方法重置摘要。一旦所有需要更新的数据都已经被更新了，
应该调用 digest 方法之一完成哈希计算。 对于给定数量的更新数据，digest 方法只能被调用一次。在调用 digest 之后，MessageDigest 对象被重新设置成其初始状态。
