---
title: Compilador advertencia (nivel 3) C4538 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4538
dev_langs:
- C++
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c4d9095eef3e37aaa487ebec9ae271bcd48c74f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075532"
---
# <a name="compiler-warning-level-3-c4538"></a>Advertencia del compilador (nivel 3) C4538

'type': no se admiten los calificadores const/volatile en este tipo

Una palabra clave de calificador se aplicó incorrectamente a una matriz. Para obtener más información, vea [Matriz](../../windows/arrays-cpp-component-extensions.md).

El ejemplo siguiente genera C4538:

```
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```