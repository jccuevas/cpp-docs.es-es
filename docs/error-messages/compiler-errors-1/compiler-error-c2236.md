---
title: Error del compilador C2236
ms.date: 11/04/2016
f1_keywords:
- C2236
helpviewer_keywords:
- C2236
ms.assetid: 0b6771a7-a783-4729-9c3d-7a3339c432cc
ms.openlocfilehash: 988377d2995468c84b86872ab6f2b25f5c3df9f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404317"
---
# <a name="compiler-error-c2236"></a>Error del compilador C2236

token inesperado 'identifier'. Compruebe si olvidó un ';'

El identificador ya está definido como un tipo y no puede reemplazarse por un tipo definido por el usuario.

El ejemplo siguiente genera el error C2236:

```
// C2236.cpp
// compile with: /c
int class A {};  // C2236 "int class" is unexpected
int i;
class B {};
```