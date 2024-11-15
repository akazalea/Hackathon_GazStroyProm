# Hackathon_GazStroyProm

Данный проект реализует способ отслеживания всех зданий, находящихся в стадии строительства. 

Используемые здесь структуры данных включают Минимальную Кучу (Min Heap) и Красно-Черные Деревья (Red Black Trees)
Исходный код имеет 3 класса, которые обеспечивают необходимую абстракцию


Структура:
Минимальная Куча и Красно-Черное Дерево связаны друг с другом указателями, указывающими в обоих направлениях на один и тот же элемент. Временная сложность поиска - O(logn), так как Красно-Черное Дерево является самобалансирующимся деревом. Временная сложность команды печати - O(logn), а команда печати диапазона - O(log(n)+S)


Архитектура системы ( Дорабатываем Ганта):

Класс Construct:
Это верхний уровень класса, который устанавливает порядок функциональности строительства. Методы, принадлежащие этому классу:
- void print(int buildingNum) //Печатает информацию о здании
- void print(int buildingNum1, int buildingNum2) //Печатает информацию о диапазоне зданий
- void insert(int buildingNum, int time) //Вставляет номера зданий и общее время в Минимальную Кучу и Красно-Черное Дерево
- construct() //Конструктор, который инициализирует счетчик и создает объекты класса Heap и класса RBT
- void syncTime(int time); Синхронизирует время между глобальным временем и счетчиком
- int dispatch(int); Отправляет здание на строительство
- int ifbuild(); Проверяет, есть ли еще здания для строительства

Класс Heap:
Этот класс обеспечивает функциональность Минимальной Кучи (Min Heap):
- heapnodeinsert(int, int, int, rbtnode); Вставляет новый узел в кучу
- struct heapnode* removeMin(); Удаляет элемент из верхушки кучи, т.е. минимальное время выполнения
- void swapbuilding(struct heapnode* a, struct heapnode*b); Меняет местами два узла в куче
- void heapify(); Восстанавливает свойство кучи
- void updateMin(int exec_time); Обновляет корневой узел и перестраивает структуру кучи
- heap(int); Объявление конструктора
- void execute(int); Функция для выполнения строительства

Класс RBT:
Этот класс отвечает за все возможности Красно-Черного Дерева:
- rbtnodeinsert(const int&n); Вставляет новый узел в дерево
- rbtnodefindnode(int bnum); Находит узел в дереве по номеру здания
- void inorder(int, int); Находит диапазон номеров зданий
- void deletenode(rbtnode*); Удаляет узел из дерева
- void fixviolation(rbtnode*); Исправляет нарушения, вызванные удалением
- void rightrotate(rbtnodep); Поворот направо после удаления
- void leftrotate(rbtnodep); Поворот налево после удаления
