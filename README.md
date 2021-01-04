# go-techLog1C
Парсер технологического журнала, основанный на стеке технологий Golang (goroutines) + Redis + Elasticsearch.

## Elasticsearch
Используется как конечная точка хранения распарсенных логов 1С. Нереляционная база данных Elasticsearch позволяет достаточно оперативно получать необходимую информацию, используя поисковые обратные индексы. В связке с Kibana - можно строить выборки, используя декларативный KSQL язык запросов. При использовании расширения XPACK (30 day free trial) можно задействовать модуль машинного обучения (Machine Learning), что позволит выявлять аномалии и различные зависимости от показателей тех журнала, например утечки памяти. 

#### Elasticsearch особенности настроек:
Elasticsearch работает на JVM, поэтому очень требователен к настройкам памяти. По умолчанию размер кучи установлен в 1Gb, что крайне мало при массовой операции вставки документов в индексы Elasticsearch. 

1.XMX/XMS рекомендуется установить равным половине оперативной памяти, доступной физической/виртуальной машине. Например, если у вас 16Gb, то возможный вариант настройки:
-Xms8000m
-Xmx8000m

[Documentation](<https://www.elastic.co/guide/en/elasticsearch/guide/master/_limiting_memory_usage.html>)
