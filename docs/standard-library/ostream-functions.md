---
title: Funciones &lt;ostream&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: "15"
manager: ghogen
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 9b9f64f67b1649c1c2f3d65f63636fd62601d06a
ms.sourcegitcommit: a7e4956c1150273e8dd39fda8b41655a6cf2cb98
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="ltostreamgt-functions"></a>Funciones &lt;ostream&gt;

Éstas son las funciones de plantilla global definidas en &lt;ostream&gt;. Para las funciones miembro, vea el [basic_ostream (clase)](basic-ostream-class.md) documentación.

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

*Elem*  
El tipo de elemento.

*Ostr*  
Un objeto de tipo **basic_ostream**.

*Tr*  
Rasgos de los caracteres.

### <a name="return-value"></a>Valor devuelto

Un objeto de tipo **basic_ostream**.

### <a name="remarks"></a>Comentarios

Las llamadas de manipulador *Ostr*.[ colocar](../standard-library/basic-ostream-class.md#put)(*Ostr*.[ ampliar](../standard-library/basic-ios-class.md#widen)('\n')) y, a continuación, se llama *Ostr*.[ Vaciar](../standard-library/basic-ostream-class.md#flush). Devuelve *Ostr*.

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

*Elem*  
El tipo de elemento.

*Ostr*  
Un objeto de tipo **basic_ostream**.

*Tr*  
Rasgos de los caracteres.

### <a name="return-value"></a>Valor devuelto

Un objeto de tipo **basic_ostream**.

### <a name="remarks"></a>Comentarios

Las llamadas de manipulador *Ostr*.[ colocar](../standard-library/basic-ostream-class.md#put)(*Elem*('\0')). Devuelve *Ostr*.

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

*Elem*  
El tipo de elemento.

*Ostr*  
Un objeto de tipo **basic_ostream**.

*Tr*  
Rasgos de los caracteres.

### <a name="return-value"></a>Valor devuelto

Un objeto de tipo **basic_ostream**.

### <a name="remarks"></a>Comentarios

Las llamadas de manipulador *Ostr*.[ Vaciar](../standard-library/basic-ostream-class.md#flush). Devuelve *Ostr*.

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

Intercambia los valores de dos **basic_ostream** objetos.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parámetros

*Elem*  
El tipo de elemento.

*Tr*  
Rasgos de los caracteres.

*left*  
Referencia lvalue a un **basic_ostream** objeto.

*right*  
Referencia lvalue a un **basic_ostream** objeto.

### <a name="remarks"></a>Comentarios

La función de plantilla **intercambio** ejecuta `left.swap(right)`.

## <a name="see-also"></a>Vea también

[\<ostream>](../standard-library/ostream.md)  
