---
title: Error del compilador C2758 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2758
dev_langs:
- C++
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ffa6d33dba70a463d789f3b0f016dc1d157eb65
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072932"
---
# <a name="compiler-error-c2758"></a>Error del compilador C2758

'member': debe inicializarse un miembro de tipo de referencia

El error del compilador C2758 se produce cuando el constructor no inicializa un miembro de tipo de referencia en una lista de inicializadores. El compilador deja el miembro sin definir. Las variables de miembro de referencia deben inicializarse cuando se declaran o se les debe dar un valor en la lista de inicialización del constructor.

El siguiente ejemplo genera el error C2758:

```
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```