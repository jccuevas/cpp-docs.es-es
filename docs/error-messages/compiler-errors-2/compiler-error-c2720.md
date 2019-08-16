---
title: Error del compilador C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: c6499fd3f279099ea7c5b31860e70bdaa285e3f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383053"
---
# <a name="compiler-error-c2720"></a>Error del compilador C2720

> '*identificador*': '*especificador*' especificador de clase de almacenamiento no es válido para miembros

La clase de almacenamiento no se puede usar en los miembros de clase externos a la declaración. Para corregir este error, quite el innecesarios [clase de almacenamiento](../../cpp/storage-classes-cpp.md) especificador de la definición del miembro fuera de la declaración de clase.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2720 y muestra cómo corregirlo:

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```