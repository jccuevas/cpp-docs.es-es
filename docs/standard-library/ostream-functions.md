---
title: Funciones &lt;ostream&gt;
ms.date: 11/04/2016
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 8d93e46b0323058d93c6d0bd8c1ee566998aef61
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447194"
---
# <a name="ltostreamgt-functions"></a>Funciones &lt;ostream&gt;

Estas son las funciones de plantilla globales definidas &lt;en&gt;ostream. Para las funciones miembro, vea la documentación de la [clase basic_ostream](basic-ostream-class.md) .

||||
|-|-|-|
|[endl](#endl)|[ends](#ends)|[flush](#flush)|
|[swap](#swap)|

## <a name="endl"></a>endl

Termina una línea y vacía el búfer.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parámetros

*Elem*\
El tipo de elemento.

*Ostr*\
Objeto de tipo **basic_ostream**.

*Anticipo*\
Rasgos de los caracteres.

### <a name="return-value"></a>Valor devuelto

Objeto de tipo **basic_ostream**.

### <a name="remarks"></a>Comentarios

El manipulador llama a *ostr*. [colocar](../standard-library/basic-ostream-class.md#put) (*Ostr*. [ampliar](../standard-library/basic-ios-class.md#widen) (' \n ')) y, a continuación, llama a *ostr*. [vaciar](../standard-library/basic-ostream-class.md#flush). Devuelve *ostr*.

### <a name="example"></a>Ejemplo

```cpp
// ostream_endl.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << endl;
}
```

```Output
testing
```

## <a name="ends"></a>extremos

Termina una cadena

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parámetros

*Elem*\
El tipo de elemento.

*Ostr*\
Objeto de tipo `basic_ostream`.

*Anticipo*\
Rasgos de los caracteres.

### <a name="return-value"></a>Valor devuelto

Objeto de tipo `basic_ostream`.

### <a name="remarks"></a>Comentarios

El manipulador llama a *ostr*. [colocar](../standard-library/basic-ostream-class.md#put) (*Elem*(' \ 0 ')). Devuelve *ostr*.

### <a name="example"></a>Ejemplo

```cpp
// ostream_ends.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "a";
   cout << "b" << ends;
   cout << "c" << endl;
}
```

```Output
ab c
```

## <a name="flush"></a>flush

Vacía el búfer.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& flush(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parámetros

*Elem*\
El tipo de elemento.

*Ostr*\
Objeto de tipo `basic_ostream`.

*Anticipo*\
Rasgos de los caracteres.

### <a name="return-value"></a>Valor devuelto

Objeto de tipo `basic_ostream`.

### <a name="remarks"></a>Comentarios

El manipulador llama a *ostr*. [vaciar](../standard-library/basic-ostream-class.md#flush). Devuelve *ostr*.

### <a name="example"></a>Ejemplo

```cpp
// ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << flush;
}
```

```Output
testing
```

## <a name="swap"></a>swap

Intercambia los valores de dos objetos `basic_ostream`.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parámetros

*Elem*\
El tipo de elemento.

*Anticipo*\
Rasgos de los caracteres.

*salido*\
Referencia lvalue a un objeto `basic_ostream`.

*correcta*\
Referencia lvalue a un objeto `basic_ostream`.

### <a name="remarks"></a>Comentarios

La función de plantilla `swap` ejecuta `left.swap(right)`.

## <a name="see-also"></a>Vea también

[\<ostream>](../standard-library/ostream.md)
