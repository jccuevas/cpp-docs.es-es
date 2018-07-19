---
title: Operadores de &lt;istream&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- istream/std::operator&gt;&gt;
dev_langs:
- C++
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60ec526dd8874529b60558f7131c31f0bf4a2d3b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961118"
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

*CH* un carácter.

*ISTR* una secuencia.

*Str* una cadena.

*Val* un tipo.

### <a name="return-value"></a>Valor devuelto

Flujo.

### <a name="remarks"></a>Comentarios

La clase `basic_istream` también define varios operadores de extracción. Para obtener más información, vea [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt).

La función de plantilla:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

extrae hasta *N* - 1 elementos y los almacena en la matriz empezando por _ *Str*. Si `Istr`. [width](../standard-library/ios-base-class.md#width) es mayor que cero, *N* es `Istr`. **ancho**; en caso contrario, es el tamaño de la matriz más grande de `Elem` que se pueden declarar. La función siempre almacena el valor `Elem()` después de cualquier elemento extraído que almacene. La extracción se detiene anticipadamente al final del archivo, en un carácter con el valor **Elem**(0) (que no se extrae) o en cualquier elemento (que no se extrae) que [ws](../standard-library/istream-functions.md#ws) descartaría. Si la función no extrae ningún elemento, llama a `Istr`. [SetState](../standard-library/basic-ios-class.md#setstate)(**failbit**). En cualquier caso, llama a `Istr`. **ancho**(0) y devuelve *Istr*.

**Nota de seguridad** la cadena terminada en null que se va a extraer el flujo de entrada no puede superar el tamaño del búfer de destino *str*. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

La función de plantilla:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

extrae un elemento, si es posible y lo almacena en *Ch*. En caso contrario, llama a **is**. [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). En cualquier caso, devuelve *Istr*.

La función de plantilla:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

devuelve `Istr` >> ( `char`**\***) `str`.

La función de plantilla:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

devuelve `Istr` >> ( **char&**) `Ch`.

La función de plantilla:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

devuelve `Istr` >> ( **char \***) `str`.

La función de plantilla:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

devuelve `Istr` >> ( **char&**) `Ch`.

La función de plantilla:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

devuelve `Istr` `>>` `val` (y convierte `rvalue reference` en `Istr` en `lvalue` durante el proceso).

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

## <a name="see-also"></a>Vea también

[\<istream>](../standard-library/istream.md)<br/>
