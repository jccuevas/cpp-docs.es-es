---
title: Error del compilador C2734
ms.date: 11/04/2016
f1_keywords:
- C2734
helpviewer_keywords:
- C2734
ms.assetid: e53a77b7-825c-42d1-a655-90e1c93b833e
ms.openlocfilehash: a188948a6d7ea7902b2df548819ffb8c40486dbc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755777"
---
# <a name="compiler-error-c2734"></a>Error del compilador C2734

' Identifier ': se debe inicializar el objeto const si no es externo

El identificador se declara `const` pero no se inicializa o `extern`.

En el ejemplo siguiente se genera C2734:

```cpp
// C2734.cpp
const int j;   // C2734
extern const int i;   // OK, declared as extern
```
