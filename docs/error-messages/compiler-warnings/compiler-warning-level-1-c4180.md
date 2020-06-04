---
title: Advertencia del compilador (nivel 1) C4180
ms.date: 11/04/2016
f1_keywords:
- C4180
helpviewer_keywords:
- C4180
ms.assetid: 40c91bd4-37f1-4d59-a4f3-d5ddab68239b
ms.openlocfilehash: f542951424325db727fc6d4ba7ac449095bdac83
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175966"
---
# <a name="compiler-warning-level-1-c4180"></a>Advertencia del compilador (nivel 1) C4180

se ha omitido el calificador aplicado al tipo de función porque no tiene ningún significado

Un calificador, como **const**, se aplica a un tipo de función definido por `typedef`.

## <a name="example"></a>Ejemplo

```cpp
// C4180.cpp
// compile with: /W1 /c
typedef int FuncType(void);

// the const qualifier cannot be applied to the
// function type FuncType
const FuncType f;   // C4180
```
