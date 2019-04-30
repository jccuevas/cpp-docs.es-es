---
title: Advertencia del compilador (nivel 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 62dfbaed28f1afcdedb41d83158dfe4e8e0f61b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384171"
---
# <a name="compiler-warning-level-1-c4945"></a>Advertencia del compilador (nivel 1) C4945

'símbolo': no se puede importar un símbolo desde 'assembly2': como "symbol" ya se ha importado desde otro ensamblado 'assembly1'

Se importó un símbolo desde un ensamblado de referencia, pero ese símbolo ya se importó desde otro ensamblado que se hace referencia. No hacer referencia a uno de los ensamblados u obtener el nombre del símbolo cambiado en uno de los ensamblados.

Los ejemplos siguientes generan C4945.

```
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Y entonces

```
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

Y entonces

```
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```