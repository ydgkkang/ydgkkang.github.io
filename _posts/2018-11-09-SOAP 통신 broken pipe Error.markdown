---
layout: post
title:  "SOAP broken pipe Exception"
date:   2018-11-09 00:18:23 +0700
categories: [ruby]
---
SOAP 통신시 broken pipe 오류가 발생했다 .왜? 나의 경우 원인은 DB I/O 처리시 발생된 이유였는데, 
xml 파싱한 데이터를 insert / update 할 경우 대량처리시 transaction 타임이 길어지게 된다. 

##### CASE1  @Async 어노테이션을 추가한 뒤 해결

{% highlight ruby %}  

    @Async("threadPoolTaskExecutor")
    @Transactional(rollbackFor = RuntimeException.class)
    public void procSoap(InputSOATest request) throws UnsupportedEncodingException {
        ...
        
    }

{% endhighlight %}  

##### CASE2 auto
{% highlight ruby %}  
application.properties 

spring.datasource.url=
jdbc:log4jdbc:mysql://jdbcUrl:4406/schema?autoReconnect=true&useSSL=false&useUnicode=true&characterEncoding=utf8&allowMultiQueries=true

{% endhighlight %}
