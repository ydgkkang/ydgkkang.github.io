---
layout: post
title:  "Java Date Type 구분"
date:   2018-11-27 11:32:04 +0700
categories: [date, java]
---

* ##### 자바 date type 작성법 정리  

  * 현재날짜 구하기
    ```
    SimpleDateFormat mSimpleDateFormat = new SimpleDateFormat ( "yyyy.MM.dd HH:mm:ss", Locale.KOREA );  
     Date Now = new Date ();  
     String current = mSimpleDateFormat.format (Now);  
    ```
     
