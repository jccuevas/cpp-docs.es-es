---
title: Asignación
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: f1697a8de3dff6c46de01db6bbff5447c03b6282
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190708"
---
# <a name="assignment"></a>Asignación

El operador de asignación ( **=** ) es, en realidad, un operador binario. La declaración es idéntica a cualquier otro operador binario, con las excepciones siguientes:

- Debe ser una función miembro no estática. No se puede declarar ningún **operador =** como una función no miembro.
- Las clases derivadas no lo heredan.
- El compilador puede generar una función **Operator =** predeterminada para los tipos de clase, si no existe ninguna.

El ejemplo siguiente muestra cómo declarar un operador de asignación:

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

El argumento proporcionado es el lado derecho de la expresión. El operador devuelve el objeto para preservar el comportamiento del operador de asignación, que devuelve el valor del lado izquierdo después de que se complete la asignación. Esto permite encadenar asignaciones, como:

```cpp
pt1 = pt2 = pt3;
```

El operador de asignación de copia no se debe confundir con el constructor de copias. Se llama a este último durante la construcción de un nuevo objeto a partir de uno existente:

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> Es aconsejable seguir la [regla de tres](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) que una clase que define un operador de asignación de copia también debe definir explícitamente el constructor de copias, el destructor y, a partir de c++ 11, el constructor de movimiento y el operador de asignación de movimiento.

## <a name="see-also"></a>Consulte también

- [Sobrecarga de operadores](../cpp/operator-overloading.md)
- [Constructores de copia y operadores de asignación de copia (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)
