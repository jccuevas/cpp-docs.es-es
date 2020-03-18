---
title: Operadores de &lt;istream&gt;
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 5ac5c61488530f99cdad38ca1bfca365b6ac0f8c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425662"
---
# <a name="ltistreamgt-operators"></a>Operadores de &lt;istream&gt;

## <a name="op_gt_gt"></a> operator&gt;&gt;

Extrae caracteres y cadenas del flujo.

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>Parámetros

\ de *CH*
Un carácter.

\ *ISTR*
Un flujo.

\ *Str*
Una cadena.

\ *Val*
Un tipo.

### <a name="return-value"></a>Valor devuelto

Flujo.

### <a name="remarks"></a>Observaciones

La clase `basic_istream` también define varios operadores de extracción. Para obtener más información, vea [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt).

La plantilla de función:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

Extrae hasta `N - 1` elementos y los almacena en la matriz a partir de *Str*. Si `Istr.`[ancho](../standard-library/ios-base-class.md#width) es mayor que cero, *N* es `Istr.width`; de lo contrario, es el tamaño de la matriz de `Elem` más grande que se puede declarar. La función siempre almacena el valor `Elem()` después de los elementos extraídos que almacena. La extracción se detiene anticipadamente al final del archivo, en un carácter con el valor `Elem(0)` (que no se extrae) o en cualquier elemento (que no se extrae) que se descartará mediante [WS](../standard-library/istream-functions.md#ws). Si la función no extrae ningún elemento, llama a `Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. En cualquier caso, llama a `Istr.width(0)` y devuelve *ISTR*.

**Nota de seguridad** La cadena terminada en null que se va a extraer del flujo de entrada no debe superar el tamaño del búfer de destino *Str*. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

La plantilla de función:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrae un elemento, si es posible, y lo almacena en *CH*. De lo contrario, llama a `is.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`. En cualquier caso, devuelve *ISTR*.

La plantilla de función:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

Devuelve `Istr >> ( char * ) str`.

La plantilla de función:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

Devuelve `Istr >> ( char& ) Ch`.

La plantilla de función:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

Devuelve `Istr >> ( char * ) str`.

La plantilla de función:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

Devuelve `Istr >> ( char& ) Ch`.

La plantilla de función:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

Devuelve `Istr >> val` (y convierte una referencia rvalue en `Istr` a un valor l en el proceso).

### <a name="example"></a>Ejemplo

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>Consulte también

[\<istream>](../standard-library/istream.md)
