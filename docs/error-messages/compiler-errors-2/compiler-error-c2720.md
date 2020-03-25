---
title: Error del compilador C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: 24f4329ee631eafc7c2670d9ebf28609c22e7592
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202145"
---
# <a name="compiler-error-c2720"></a>Error del compilador C2720

> '*Identifier*': el especificador de clase de almacenamiento '*Specifier*' no es válido en los miembros

La clase de almacenamiento no se puede usar en los miembros de clase externos a la declaración. Para corregir este error, quite el especificador de [clase de almacenamiento](../../cpp/storage-classes-cpp.md) innecesario de la definición del miembro fuera de la declaración de clase.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2720 y muestra cómo corregirlo:

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```
