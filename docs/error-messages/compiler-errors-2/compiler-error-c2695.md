---
title: Error del compilador C2695 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2695
dev_langs:
- C++
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a618c02fcf3a8927d8090b1ad51ed16d9ac28542
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056058"
---
# <a name="compiler-error-c2695"></a>Error del compilador C2695

'function1': reemplazar la función virtual difiere de 'función2' sólo por convención de llamada

La firma de una función en una clase derivada no puede reemplazar una función en una clase base y cambiar la convención de llamada.

El ejemplo siguiente genera C2695:

```
// C2695.cpp
class C {
   virtual void __fastcall func();
};

class D : public C {
   virtual void __clrcall func();   // C2695
};
```