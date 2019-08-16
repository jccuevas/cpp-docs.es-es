---
title: Error del compilador C2364
ms.date: 11/04/2016
f1_keywords:
- C2364
helpviewer_keywords:
- C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
ms.openlocfilehash: 051468ea861190dd3f6a28dc272f1bab155145af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230404"
---
# <a name="compiler-error-c2364"></a>Error del compilador C2364

'type': tipo no válido para el atributo personalizado

Argumentos con nombre para los atributos personalizados se limitan a constantes en tiempo de compilación. Por ejemplo, los tipos enteros (int, char, etc.), System:: Type ^ y System:: Object ^.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2364.

```
// c2364.cpp
// compile with: /clr /c
using namespace System;

[attribute(AttributeTargets::All)]
public ref struct ABC {
public:
   // Delete the following line to resolve.
   ABC( Enum^ ) {}   // C2364
   ABC( int ) {}   // OK
};
```