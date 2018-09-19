---
title: Error del compilador C2032 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ab02ca695ec94f25054e3490232b782a46a53a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064014"
---
# <a name="compiler-error-c2032"></a>Error del compilador C2032

'identifier': función no puede ser miembro del struct/union 'estructuraounión'

La estructura o unión tiene una función miembro, que se admite en C++, pero no en C. Para resolver el error, compile como un programa de C++ o quite la función miembro.

El ejemplo siguiente genera C2032:

```
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

Posible resolución:

```
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```