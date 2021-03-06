.. _transport:

==================
Cетевые транспорты
==================

Что такое транспорт
===================

Транспортом в Grab называется расширение, которое осуществляет сетевой запрос и обработку полученного ответа. Grab предоставляет универсальный интерфейс для настройки параметра запроса и для обработки результатов запроса, но сама функциональность по отсылке и приёму данных по сетевому каналу скрыта внутри библиотеки и может осуществляться различными способами.

Транспорт pycurl
================

Сайт библиотеки: http://pycurl.sourceforge.net

По-умолчанию, Grab работает с библиотекой pycurl, это python-интерфейс к библиотеке `cURL <http://curl.haxx.se/>`_. Библиотека curl поддерживает огромное количество возможностей по создания, передаче и получению HTTP-запросов. Библиотека curl не ограничена работой с HTTP-протоколом, но Grab в основном ориентирован на HTTP-протокол. Схема использования pycurl в Grab довольно проста: в аттрибуте `pycurl` хранится pycurl объект, который настраивается в соотвествии с заданными опциями и затем используется для передачи данных на сервер и приёма ответных данных. Интерфейс библиотеки pycurl не слишком удобный, собственно, это и было изначальной причиной написать Grab - получить человечкий интерфейс к возможностям curl.

Транспорт urllib
================

Cайт библиотеки: http://docs.python.org/library/urllib.html

Преимуществом этого транспорта является то, что библиотека urllib является стандартной библиотекой языка python. Разработка данного транспорта находится в зачаточном состоянии. На данный момент я попытался использовать urllib через прослойку Requests, возможно, следует отказаться от неё и соединить Grab и urllib напрямую.

Транспорт selenium
==================

Сайт библиотеки: http://seleniumhq.org/

Преимуществом данного транспорта является то, что selenium позволяет работать с документами в режиме браузера, в том числе выполнять javascript скрипты. На данный момент транспорт seleinum находится в очень `зачаточном состоянии <https://bitbucket.org/lorien/grab/src/0715ec5c6636/grab/transport/selenium.py>`_. Пощупать можно так::

    from grab import GrabSelenium

    g = GrabSelenium()
    g.go('http://ixbt.com')
    print g.xpath_text('//title')

Ествественно вам нужно установить предварительно selenium. Это можно сделать командой: `sudo pip install selenium`.
