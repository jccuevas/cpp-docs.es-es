---
title: Sobrecarga de operadores de incremento y decremento (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: 40ae12130fdced9fd958c3b8316fa3b718ca9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374127"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Sobrecarga de operadores de incremento y decremento (C++)

Los operadores de incremento y decremento pertenecen a una categoría especial porque hay dos variantes de cada uno de ellos:

- Preincremento y postincremento

- Predecremento y postdecremento

Cuando escriba funciones de operador sobrecargadas, puede resultarle útil implementar versiones distintas para las versiones de prefijo y de postfijo de estos operadores. Para distinguir entre los dos, se observa la siguiente regla: La forma de prefijo del operador se declara exactamente de la misma manera que cualquier otro operador unario; el formulario de postfijo acepta un argumento adicional de tipo **int**.

> [!NOTE]
> Al especificar un operador sobrecargado para la forma de postfijo del operador de incremento o decremento, el argumento adicional debe ser de tipo **int**; especificar cualquier otro tipo genera un error.

En el ejemplo siguiente se muestra cómo definir operadores de incremento y decremento de prefijo y de postfijo para la clase `Point`:

```cpp
// increment_and_decrement1.cpp
class Point
{
public:
   // Declare prefix and postfix increment operators.
   Point& operator++();       // Prefix increment operator.
   Point operator++(int);     // Postfix increment operator.

   // Declare prefix and postfix decrement operators.
   Point& operator--();       // Prefix decrement operator.
   Point operator--(int);     // Postfix decrement operator.

   // Define default constructor.
   Point() { _x = _y = 0; }

   // Define accessor functions.
   int x() { return _x; }
   int y() { return _y; }
private:
   int _x, _y;
};

// Define prefix increment operator.
Point& Point::operator++()
{
   _x++;
   _y++;
   return *this;
}

// Define postfix increment operator.
Point Point::operator++(int)
{
   Point temp = *this;
   ++*this;
   return temp;
}

// Define prefix decrement operator.
Point& Point::operator--()
{
   _x--;
   _y--;
   return *this;
}

// Define postfix decrement operator.
Point Point::operator--(int)
{
   Point temp = *this;
   --*this;
   return temp;
}
int main()
{
}
```

Pueden definirse los mismos operadores en el ámbito de archivo (global) mediante los siguientes encabezados de función:

```cpp
friend Point& operator++( Point& )      // Prefix increment
friend Point& operator++( Point&, int ) // Postfix increment
friend Point& operator--( Point& )      // Prefix decrement
friend Point& operator--( Point&, int ) // Postfix decrement
```

El argumento de tipo **int** que denota la forma de postfijo del operador de incremento o decremento no se utiliza normalmente para pasar argumentos. Normalmente contiene el valor 0. Sin embargo, se puede utilizar del modo siguiente:

```cpp
// increment_and_decrement2.cpp
class Int
{
public:
    Int &operator++( int n );
private:
    int _i;
};

Int& Int::operator++( int n )
{
    if( n != 0 )    // Handle case where an argument is passed.
        _i += n;
    else
        _i++;       // Handle case where no argument is passed.
    return *this;
}
int main()
{
   Int i;
   i.operator++( 25 ); // Increment by 25.
}
```

No hay ninguna sintaxis para usar los operadores de incremento y decremento para pasar estos valores que no sea la invocación explícita, como se muestra en el código anterior. Una forma más sencilla de implementar esta funcionalidad es**+=** sobrecargar el operador de adición/asignación ( ).

## <a name="see-also"></a>Consulte también

[Sobrecarga del operador](../cpp/operator-overloading.md)
