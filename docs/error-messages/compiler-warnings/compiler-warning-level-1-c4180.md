---
title: Advertencia del compilador (nivel 1) C4180
ms.date: 11/04/2016
f1_keywords:
- C4180
helpviewer_keywords:
- C4180
ms.assetid: 40c91bd4-37f1-4d59-a4f3-d5ddab68239b
ms.openlocfilehash: 1fd56f3bcc662a326e4a263bb0a266ffc37d6ec6
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626241"
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