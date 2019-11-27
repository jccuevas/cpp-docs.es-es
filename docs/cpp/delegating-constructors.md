---
title: Delegar constructores (C++)
description: Use los constructores de delegación C++ en para invocar a otros constructores y reducir la repetición del código.
ms.date: 11/19/2019
ms.openlocfilehash: 533cdfbeb882f3770cc554b0633611a4ffc2cfbd
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250701"
---
# <a name="delegating-constructors"></a>Constructores de delegación

Muchas clases tienen varios constructores que realizan acciones similares, por ejemplo, validan parámetros:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c() {}
    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
        middle = my_middle < max && my_middle > min ? my_middle : 5;
    }
};
```

Puede reducir el código repetitivo si agrega una función que realice toda la validación, pero el código de `class_c` sería más fácil de entender y mantener si un constructor pudiera delegar alguna parte del trabajo en otro. Para agregar la delegación de constructores, utilice la sintaxis `constructor (. . .) : constructor (. . .)`:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) : class_c(my_max) {
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){
        middle = my_middle < max && my_middle > min ? my_middle : 5;
}
};
int main() {

    class_c c1{ 1, 3, 2 };
}
```

A medida que recorra paso a paso el ejemplo anterior, observe que el constructor `class_c(int, int, int)` llama primero al constructor `class_c(int, int)`, que a su vez llama a `class_c(int)`. Cada uno de los constructores realiza solo el trabajo que no realizan los otros constructores.

El primer constructor al que se llama inicializa el objeto para que todos sus miembros se inicialicen en ese momento. No se puede realizar la inicialización de miembro en un constructor que delega en otro constructor, tal como se muestra aquí:

```cpp
class class_a {
public:
    class_a() {}
    // member initialization here, no delegate
    class_a(string str) : m_string{ str } {}

    //can’t do member initialization here
    // error C3511: a call to a delegating constructor shall be the only member-initializer
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}

    // only member assignment
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string;
};
```

En el ejemplo siguiente se muestra el uso de los inicializadores de miembro de datos no estático. Observe que, si un constructor inicializa también un miembro de datos determinado, el inicializador de miembro se invalida:

```cpp
class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };
};

int main() {
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"
    int y = 4;
}
```

La sintaxis de delegación de constructores no impide la creación accidental de recursividad de constructores (el Constructor1 llama al Constructor2, que llama al Constructor1) y no se genera ningún error hasta que se produzca un desbordamiento de pila. Es responsabilidad del programador evitar los ciclos.

```cpp
class class_f{
public:
    int max;
    int min;

    // don't do this
    class_f() : class_f(6, 3){ }
    class_f(int my_max, int my_min) : class_f() { }
};
```
