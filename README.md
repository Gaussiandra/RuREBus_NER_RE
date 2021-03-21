Решение дорожки RuREBus в рамках [DIALOGUE EVALUATION 2020](http://www.dialog-21.ru/evaluation/2020/disambiguation/rurebus/) - соревнованию по извлечению отношений в бизнес-постановке. В качестве датасета использовались документы минестерства экономического развития, в котором было 17 типов именованных сущностей и 12 типов связей.
##### Пример данных
![Снимок](https://user-images.githubusercontent.com/34653515/111898184-9608f000-8a35-11eb-8821-607c72b857d9.PNG)

* Для задачи NER использовалась архитектура **CharCNN + ELMO embeddings -> BLSTM -> CRF**, что в результате дало 0.492 F1.
* Задача RE решалась архитектурой, схожей с описанной в этой [статье](https://www.aclweb.org/anthology/P16-1072.pdf): Две головы, состоящие из **CharCNN + ELMO embeddings -> BLSTM -> CNN -> Linear**. В одну подаётся предложение в исходном виде, во вторую в порядке, определяемом синтаксическим разбором -- кратчайшим путём в графе разбора между рассматриваемой парой слов. В лоссе учитывается выход каждой головы, а также выход, получаемый объединением признаков с этих голов. Описанный подход даёт 0.33 F1 на тестовых данных.
![Снимок](https://user-images.githubusercontent.com/34653515/111900916-3109c600-8a46-11eb-8543-ab271e630458.PNG) 
