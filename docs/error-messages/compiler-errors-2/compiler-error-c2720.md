---
title: Error del compilador C2720 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2720
dev_langs:
- C++
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d75c9847016102d4ae8609fb0a0a78726e4c67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084021"
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