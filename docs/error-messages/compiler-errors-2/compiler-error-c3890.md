---
title: Error del compilador C3890 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3890
dev_langs:
- C++
helpviewer_keywords:
- C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e599150c1e8d62d751f9dca67cffc99fb079bd32
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104929"
---
# <a name="compiler-error-c3890"></a>Error del compilador C3890

'var': no puede tomar la dirección de un miembro de datos literal

Existe un miembro de datos literal en el montón de recolección.  Un objeto en el montón de recolección se puede mover, por lo que no es útil tomar la dirección.

El ejemplo siguiente genera C3890:

```
// C3890.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   int p = &Y1::staticConst;   // C3890
   int p2 = Y1::staticConst;   // OK
}
```