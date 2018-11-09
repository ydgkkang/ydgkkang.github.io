---
layout: post
title:  "SOAP broken pipe Exception"
date:   2018-11-09 00:18:23 +0700
categories: [ruby]
---
SOAP 통신시 broken pipe 오류가 발생했다 .왜? 나의 경우 원인은 DB I/O 처리시 발생된 이유였는데, 
xml 파싱한 데이터를 insert / update 할 경우 대량처리시 transaction 타임이 길어지게 된다. 

@Async 어노테이션을 추가한 뒤 해결

{% highlight ruby %}
#!/usr/bin/env ruby

require 'json'
require 'net/http'
require 'libnotify'

def parsejson
    file = "http://api.openweathermap.org/data/2.5/find?q=London&mode=json"
    response = Net::HTTP.get_response(URI.parse(file))
    weatherjson = response.body
    actual = JSON.parse(weatherjson)

    # check for errors
    if actual.has_key? 'Error'
        raise "error with the url"
    end

    results = []

    actual["list"].each do |listitem|
        weather = listitem["weather"]
        weather.each do |weath|
            results.push(weath["description"])
        end
        main = listitem["main"]
        temp = main["temp"] - 273.15
        results.push ("%.2f" % temp)
    end

    return results
end
{% endhighlight %}
