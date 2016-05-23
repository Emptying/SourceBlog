---
title: Java JDBC基本连接
p: ./java
date: 2016-05-18 00:24:21
tags:
  - java
category: android
---




``` java

package com.empty.jdbc;

import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class JdbcDemo {

	public static void main(String[] args) {
		//数据库连接
		Connection connection = null;
		//数据库操作
		Statement statement = null;
		//数据库结果
		ResultSet result = null;
		//使用jdbc驱动
		try {
			Class.forName("com.mysql.jdbc.Driver");
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		}
		//创建数据库连接
		try {
			connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/student?useSSL=false","root","password");
		} catch (SQLException e) {
			e.printStackTrace();
		}
		//创建数据库操作
		try {
			statement = connection.createStatement();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		//得到数据库操作结果集
		try {
			statement.execute("delete from user where name='王五'");
			result = statement.executeQuery("select * from user");
		} catch (SQLException e) {
			e.printStackTrace();
		}
		//
		try {
			while(result.next()){
				System.out.print("ID:"+result.getInt("ID")+" ");
				System.out.print("名字:"+result.getString("name")+" ");
				System.out.print("密码:"+result.getString("password")+" ");
				System.out.println("年龄:"+result.getInt("age"));
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}finally {
			
			try {
				connection.close();
				statement.close();
				result.close();
			} catch (SQLException e) {
				e.printStackTrace();
			}
		}

	}

}

```


