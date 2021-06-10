# DockerPipelineNew

Для запуска пайплайна необходимо:
* Склонировать данный репозиторий к себе на компьютер
* Установить docker-compose
* В склонированном репозитории в директории pipeline выполнить команду "sudo docker-compose build"
* Там же выполнить команду "sysctl -w vm.max_map_count=262144"
* В той же директории выполнить команду "sudo docker-compose up"
* Дождаться запуска всех контейнеров
* В отдельном окне терминала в той же директории pipeline выполнить команду "curl -X POST "localhost:5601/api/saved_objects/_import" -H "kbn-xsrf: true" --form file=@export.ndjson" для загрузки конфигурации дашборда и индексов в Kibana

Далее можно открыть GoCD в браузере по адресу localhost:8153 и начать обучение модели нажатием на кнопку "play" в ModelFit. После обучения модели ее веса будут видны в UI Kibana по адресу localhost:5601/app/discover, индекс logstash_train_log-\*. Приложение на Flask доступно по адресу localhost:5100, при отправке заполненной формы через него будет выдано предсказание модели для введенных данных, а также указанные данные будут доступны в виде логов в том же UI Kibana, индекс logstash_app_log-\*, и отображены в дашборде по адресу localhost:5601/app/dashboards, дашборд App logs. 
