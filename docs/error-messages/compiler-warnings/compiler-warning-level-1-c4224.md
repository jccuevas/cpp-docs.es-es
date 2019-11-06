---
title: ADVERTENCIA del compilador (nivel 1) C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: 2ac7c49f33c052c895c71ca1dc3ce60be8dd9c8d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627292"
---
# <a name="compiler-warning-level-1-c4224"></a>ADVERTENCIA del compilador (nivel 1) C4224

se ha utilizado una extensión no estándar: el parámetro formal ' Identifier ' se definió previamente como un tipo

El identificador se usó previamente como `typedef`. Esto produce una advertencia en la compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Ejemplo

```cpp
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```