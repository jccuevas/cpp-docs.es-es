---
title: Error del compilador C3638 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3638
dev_langs:
- C++
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f1d135dd69155de39b097d59cf139eb47354d4f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107690"
---
# <a name="compiler-error-c3638"></a>Error del compilador C3638

'operador': no se puede redefinir la conversión boxing estándar y los operadores de conversión unboxing

El compilador define un operador de conversión para cada clase administrada para admitir la conversión boxing implícita. Este operador no se puede redefinir.

Para obtener más información, consulte [conversión Boxing implícita](../../windows/boxing-cpp-component-extensions.md).

El ejemplo siguiente genera C3638:

```
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```