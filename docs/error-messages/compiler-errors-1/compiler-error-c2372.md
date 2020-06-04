---
title: Error del compilador C2372
ms.date: 03/23/2020
f1_keywords:
- C2372
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
ms.openlocfilehash: 4d60f93def9bfe8359496803c8aede1ec698b465
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150945"
---
# <a name="compiler-error-c2372"></a>Error del compilador C2372

> '*Identifier*': nueva definición; distintos tipos de direccionamiento indirecto

El identificador ya está definido con un tipo derivado diferente.

En el ejemplo siguiente se genera C2372:

```cpp
// C2372.cpp
// compile with: /c
extern int *fp;
extern int fp[];   // C2372
extern int fp2[];   // OK
```
