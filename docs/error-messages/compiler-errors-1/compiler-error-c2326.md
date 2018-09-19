---
title: Error del compilador C2326 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2326
dev_langs:
- C++
helpviewer_keywords:
- C2326
ms.assetid: 01a5ea40-de83-4e6f-a4e8-469f441258e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb81b429e88bd364d6e4d649bd28234ed829a930
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063975"
---
# <a name="compiler-error-c2326"></a>Error del compilador C2326

'declarador': la función no puede acceder a 'nombre'

El código intenta modificar una variable de miembro, lo cual no es posible.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2326:

```
// C2326.cpp
void MyFunc() {
   int i;

   class MyClass  {
   public:
      void mf() {
         i = 4;   // C2326 i is inaccessible
      }
   };
}
```