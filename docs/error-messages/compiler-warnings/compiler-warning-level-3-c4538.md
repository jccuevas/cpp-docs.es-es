---
title: Advertencia del compilador (nivel 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: e0f20c7b1d9f840bc272cd3b9d43f4872ac3f71d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779237"
---
# <a name="compiler-warning-level-3-c4538"></a>Advertencia del compilador (nivel 3) C4538

'type': no se admiten los calificadores const/volatile en este tipo

Una palabra clave de calificador se aplicó incorrectamente a una matriz. Para obtener más información, vea [Matriz](../../extensions/arrays-cpp-component-extensions.md).

El ejemplo siguiente genera C4538:

```
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```