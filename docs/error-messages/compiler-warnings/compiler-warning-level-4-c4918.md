---
title: Advertencia del compilador (nivel 4) C4918
ms.date: 11/04/2016
f1_keywords:
- C4918
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
ms.openlocfilehash: 801c22a45037492dc609d93c6339ab8feff30494
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988806"
---
# <a name="compiler-warning-level-4-c4918"></a>Advertencia del compilador (nivel 4) C4918

'character': carácter no válido en la lista de optimizaciones de pragma

Se encontró un carácter desconocido en la lista de optimizaciones de una instrucción pragma [optimize](../../preprocessor/optimize.md) .

Por ejemplo, la siguiente instrucción genera la advertencia C4918:

```cpp
// C4918.cpp
// compile with: /W4
#pragma optimize("X", on) // C4918 expected
int main()
{
}
```
