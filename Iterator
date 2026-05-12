class FlatIterator:

    def __init__(self, list_of_list):
        # Сохраняем исходный список списков
        self._list = list_of_list
        # Индексы для навигации: внешний (текущий подсписок) и внутренний (элемент в нём)
        self._outer = 0
        self._inner = 0

    def __iter__(self):
        # Итератор является собственным итератором
        return self

    def __next__(self):
        # Продолжаем, пока есть подсписки
        while self._outer < len(self._list):
            current_sublist = self._list[self._outer]
            # Если есть элементы в текущем подсписке — берём следующий
            if self._inner < len(current_sublist):
                item = current_sublist[self._inner]
                self._inner += 1
                return item
            else:
                # Подсписок закончился, переходим к следующему
                self._outer += 1
                self._inner = 0
        # Если подсписки кончились — итерация завершена
        raise StopIteration


def test_1():
    list_of_lists_1 = [
        ['a', 'b', 'c'],
        ['d', 'e', 'f', 'h', False],
        [1, 2, None]
    ]

    for flat_iterator_item, check_item in zip(
            FlatIterator(list_of_lists_1),
            ['a', 'b', 'c', 'd', 'e', 'f', 'h', False, 1, 2, None]
    ):
        assert flat_iterator_item == check_item

    assert list(FlatIterator(list_of_lists_1)) == ['a', 'b', 'c', 'd', 'e', 'f', 'h', False, 1, 2, None]


if __name__ == '__main__':
    test_1()
