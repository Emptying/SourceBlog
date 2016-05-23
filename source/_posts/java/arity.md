---
title: java使用arity计算器引擎
p: ./java
date: 2016-05-22 20:15:21
tags:
  - java
category: android
---




``` java
package com.empty.calculator;

import org.javia.arity.Symbols;
import org.javia.arity.SyntaxException;
import org.junit.Test;

/**
 * To work on unit tests, switch the Test Artifact in the Build Variants view.
 */
public class ExampleUnitTest {

    @Test
    public void testExpresion() throws SyntaxException {
        Symbols symbols = new Symbols();
		//直接把表达式放进去
		double result=symbols.eval("1+2/3");
        System.out.println(""+result);
    }

}


```
> arity下载地址: https://raw.githubusercontent.com/Emptying/Calculator/master/app/libs/arity-2.1.2.jar
> 具体使用例子 https://github.com/Emptying/Calculator