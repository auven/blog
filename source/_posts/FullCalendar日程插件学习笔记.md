---
title: FullCalendar日程插件学习笔记
date: 2017-07-27 15:16:00
tags: 
- 前端插件
categories:
- 前端插件
---

> 本文只记录一些特殊的方法方案，简单的使用请查看[官方文档](https://fullcalendar.io/docs/)

### `dayClick`获取点击日期的所有日程

```js
dayClick: function (date, jsEvent, view, resourceObj) {

    alert('Clicked on: ' + date.format());

    alert('Coordinates: ' + jsEvent.pageX + ',' + jsEvent.pageY);

    alert('Current view: ' + view.name);

    console.log(full);

    // change the day's background color just for fun
    $(this).css('background-color', 'red');

    var events = $('#calendar').fullCalendar('clientEvents', function (event) {
        var eventStart = event.start.format('YYYY-MM-DD');
        var eventEnd = event.end ? event.end.format('YYYY-MM-DD') : null;
        var theDate = date.format('YYYY-MM-DD');
        // Make sure the event starts on or before date and ends afterward
        // Events that have no end date specified (null) end that day, so check if start = date
        return (eventStart <= theDate && (eventEnd >= theDate) && !(eventStart < theDate && (eventEnd == theDate))) || (eventStart == theDate && (eventEnd === null));
    });
    console.log(events); // do whatever with the events
}
```

参考：https://www.douban.com/note/559785873/
