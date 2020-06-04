---
title: Operadores de &lt;istream&gt;
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 3b9521fde1b5a03389bfc1ad3e35fa407d9d6ac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363035"
---
# <a name="ltistreamgt-operators"></a>Operadores de &lt;istream&gt;

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>Operador&gt;&gt;

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

*Ch*\
Un carácter.

*Istr*\
Flujo.

*Str*\
Una cadena.

*Val*\
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

extrae hasta `N - 1` los elementos y los almacena en la matriz a partir de *str*. Si `Istr.` [width](../standard-library/ios-base-class.md#width) es mayor que cero, *N* es `Istr.width`; de lo contrario, es el tamaño `Elem` de la matriz más grande de la que se puede declarar. La función siempre `Elem()` almacena el valor después de los elementos extraídos que almacena. La extracción se detiene al principio `Elem(0)` del final del archivo, en un carácter con valor (que no se extrae) o en cualquier elemento (que no se extraiga) que se descartaría por [ws](../standard-library/istream-functions.md#ws). Si la función no extrae ningún elemento, llama a `Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`. En cualquier caso, `Istr.width(0)` llama y devuelve *Istr*.

**Nota de seguridad** La cadena terminada en null que se extrae de la secuencia de entrada no debe superar el tamaño del búfer de destino *str*. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

La plantilla de función:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrae un elemento, si es posible, y lo almacena en *Ch*. De lo `is.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`contrario, llama a . En cualquier caso, devuelve *Istr*.

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

devuelve `Istr >> val` (y convierte una referencia `Istr` rvalue a un valor l en el proceso).

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

[\<>istream](../standard-library/istream.md)
