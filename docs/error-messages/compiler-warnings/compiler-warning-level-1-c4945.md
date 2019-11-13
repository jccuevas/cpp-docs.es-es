---
title: ADVERTENCIA del compilador (nivel 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 6a20effcebe1a36fa1356fffefa3a23a0056a0f0
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052255"
---
# <a name="compiler-warning-level-1-c4945"></a>ADVERTENCIA del compilador (nivel 1) C4945

' Symbol ': no se puede importar el símbolo desde ' assembly2 ': ya se ha importado ' Symbol ' desde otro ensamblado ' Assembly1 '

Se importó un símbolo de un ensamblado al que se hace referencia, pero ese símbolo ya se importó desde otro ensamblado al que se hace referencia. No haga referencia a uno de los ensamblados u obtenga el nombre del símbolo cambiado en uno de los ensamblados.

Los ejemplos siguientes generan C4945.

```csharp
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

y, a continuación,

```csharp
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

y, a continuación,

```cpp
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```