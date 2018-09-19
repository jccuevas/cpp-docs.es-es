---
title: Del compilador (nivel 1) de la advertencia C4926 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4926
dev_langs:
- C++
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1942c334f06dce7a8f208f01cae6e2da1b6bb6cf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087947"
---
# <a name="compiler-warning-level-1-c4926"></a>Advertencia del compilador (nivel 1) C4926

'identificador': ya se ha definido el símbolo: se han omitido los atributos.

Se encontró una declaración adelantada, pero ya existe una construcción con atributos con el mismo nombre. Se omiten los atributos de la declaración adelantada.

El ejemplo siguiente genera la advertencia C4926:

```
// C4926.cpp
// compile with: /W1
[module(name="MyLib")];

[coclass]
struct a {
};

[coclass]
struct a;   // C4926

int main() {
}
```