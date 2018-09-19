---
title: Error del compilador C3152 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3152
dev_langs:
- C++
helpviewer_keywords:
- C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 975ce5a948305f5b2538496ddef34e18bb6db63c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079692"
---
# <a name="compiler-error-c3152"></a>Error del compilador C3152

'construct': 'keyword' solo se puede aplicar a una función de clase, struct o miembro virtual

Algunas palabras clave solo se pueden aplicar a una clase de C++.

En el ejemplo siguiente se genera el error C3152 y se muestra cómo corregirlo.

```
// C3152.cpp
// compile with: /clr /c
ref class C {
   int (*pfn)() sealed;   // C3152
   virtual int g() sealed;   // OK
};
```
