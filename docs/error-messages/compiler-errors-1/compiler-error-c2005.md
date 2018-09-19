---
title: Error del compilador C2005 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2005
dev_langs:
- C++
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6dfba3b960a046bf40751c135c3b99fbe843545
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100687"
---
# <a name="compiler-error-c2005"></a>Error del compilador C2005

\#línea esperaba un número de línea, que pero se encontró 'token'

El `#line` directiva debe ir seguida por un número de línea.

El ejemplo siguiente genera C2005:

```
// C2005.cpp
int main() {
   int i = 0;
   #line i   // C2005
}
```

Posible resolución:

```
// C2005b.cpp
int main() {
   int i = 0;
   #line 0
}
```