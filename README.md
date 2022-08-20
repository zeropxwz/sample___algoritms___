## Алгоритмы поиска  

### Линейный поиск  

Осуществляется методом последовательного перебора всех элементов массива, пока не найдет нужный или не пройдет по всему массиву.  

##### Сложность: O(N)

#### Линейный поиск на TypeScript:

```ts
function linearSearch<A>(list: Array<A>, item: A): A | null {
    for (let i = 0; i < list.length; i++) {
        if (list[i] === item) {
            return list[i]
        }
    }

    return null
}
```

#### Линейный поиск на python:

```py
def linearSearch (list, item):
    for i in range(len(list)):
        if (list[i] == item):
            return list[i]

    return None
```

## Двунаправленный поиск

Похож на обычный линейный поиск, но отличается тем, что последовательность поиска ведется сразу с двух направлений - с начала и с конца массива.  
##### Сложность: O(N)

#### Двунаправленный поиск на TypeScript:

```ts
function biDirectSearch<A>(list: Array<A>, item: A): A | null {

    let l: number = 0
    let r: number = list.length - 1

    while (l < list.length / 2) {
        if (list[l] === item) return list[l]
        if (list[r] === item) return list[r]

        l++
        r--
    }

    return null
}
```

#### Двунаправленный поиск на python:

```py
def biDirectSearch (list, item):

    l = 0
    r = 0

    length = len(list) / 2
    
    while (l <= length):
        if (list[l] == item): 
            return list[l]
        if (list[r] == item):
            return list[r]

        l += 1
        r -= 1

    return None
```

### бинарный поиск

Массив делится на две части - левую и праую. Если искомое значение меньше, чем значение центрального элемента, то правая часть отбрасывается и поиск продолжается, только в левой. На следуйшей итерации операция повтаряется. Так до тех пор центральный элемент (указатель) не будет равен искомому или все элементы не будут проверены.  

##### сложность: O(LOG2N)  

<img src="assets/binary-search.png" width="720">

#### бинарный поиск на TypeScript  

```ts
function binarySearch<A>(list: Array<A>, item: A): A | null {

    let left:  number = 0
    let right: number = list.length

    let point: number

    while (true) {

        point = Math.floor( (left + right) / 2 )

        if (list[point] === item) {
            return list[point]
        }
        if (left + 1 === right) {
            return null
        }

        if (item < list[point]) {
            right = point
        }
        else {
            left = point
        }
    }
}
```

