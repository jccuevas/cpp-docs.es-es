---
title: Funciones &lt;ostream&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 494c750ec80000ef9090824e0436f6e443593847
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107619"
---
# <a name="ltostreamgt-functions"></a>Funciones &lt;ostream&gt;

Estas son las funciones de plantilla global definidas en &lt;ostream&gt;. Para las funciones miembro, vea el [basic_ostream (clase)](basic-ostream-class.md) documentación.

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

*Elem*<br/>
El tipo de elemento.

*Ostr*<br/>
Un objeto de tipo **basic_ostream**.

*Tr*<br/>
Rasgos de los caracteres.

### <a name="return-value"></a>Valor devuelto

Un objeto de tipo **basic_ostream**.

### <a name="remarks"></a>Comentarios

El manipulador llama a *Ostr*.[ colocar](../standard-library/basic-ostream-class.md#put)(*Ostr*.[ ampliar](../standard-library/basic-ios-class.md#widen)('\n')) y, a continuación, llama a *Ostr*.[ Vaciar](../standard-library/basic-ostream-class.md#flush). Devuelve *Ostr*.

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

*Elem*<br/>
El tipo de elemento.

*Ostr*<br/>
Objeto de tipo `basic_ostream`.

*Tr*<br/>
Rasgos de los caracteres.

### <a name="return-value"></a>Valor devuelto

Objeto de tipo `basic_ostream`.

### <a name="remarks"></a>Comentarios

El manipulador llama a *Ostr*.[ colocar](../standard-library/basic-ostream-class.md#put)(*Elem*('\0')). Devuelve *Ostr*.

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

*Elem*<br/>
El tipo de elemento.

*Ostr*<br/>
Objeto de tipo `basic_ostream`.

*Tr*<br/>
Rasgos de los caracteres.

### <a name="return-value"></a>Valor devuelto

Objeto de tipo `basic_ostream`.

### <a name="remarks"></a>Comentarios

El manipulador llama a *Ostr*.[ Vaciar](../standard-library/basic-ostream-class.md#flush). Devuelve *Ostr*.

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

*Elem*<br/>
El tipo de elemento.

*Tr*<br/>
Rasgos de los caracteres.

*left*<br/>
Referencia lvalue a un objeto `basic_ostream`.

*right*<br/>
Referencia lvalue a un objeto `basic_ostream`.

### <a name="remarks"></a>Comentarios

La función de plantilla `swap` ejecuta `left.swap(right)`.

## <a name="see-also"></a>Vea también

[\<ostream>](../standard-library/ostream.md)
