---
title: Advertencia del compilador (nivel 1) C4810
ms.date: 11/04/2016
f1_keywords:
- C4810
helpviewer_keywords:
- C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
ms.openlocfilehash: bdeb4dd28587635a391e7b776ccd88b637a7769f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174939"
---
# <a name="compiler-warning-level-1-c4810"></a>Advertencia del compilador (nivel 1) C4810

valor de pragma pack(show) == n

Esta advertencia se emite cuando se usa la opción **show** de pragma [pack](../../preprocessor/pack.md) . *n* es el valor actual de pack.

Por ejemplo, el código siguiente muestra cómo funciona la advertencia C4810 con pragma pack:

```cpp
// C4810.cpp
// compile with: /W1 /LD
// C4810 expected
#pragma pack(show)
#pragma pack(4)
#pragma pack(show)
```
