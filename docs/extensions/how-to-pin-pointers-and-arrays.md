---
title: 'Cómo: Anclar punteros y matrices'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
ms.openlocfilehash: 8dc42690f0f56b97b2af3ed54dfb17d49b081695
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172222"
---
# <a name="how-to-pin-pointers-and-arrays"></a>Cómo: Anclar punteros y matrices

Anclar un subobjeto definido en un objeto administrado tiene el efecto de anclar todo el objeto.  Por ejemplo, si se ancla cualquier elemento de una matriz, también se anclará toda la matriz. No hay ninguna extensión para el lenguaje para declarar una matriz anclada. Para anclar una matriz, declare un puntero anclado a su tipo de elemento y ancle uno de sus elementos.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
// pin_ptr_array.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

int main() {
   array<Byte>^ arr = gcnew array<Byte>(4);
   arr[0] = 'C';
   arr[1] = '+';
   arr[2] = '+';
   arr[3] = '\0';
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned
   unsigned char * cp = p;

   printf_s("%s\n", cp); // bytes pointed at by cp
                         // will not move during call
}
```

```Output
++
```

## <a name="see-also"></a>Consulte también

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)
