---
title: Error del compilador C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: fdfd2200503f80addb120117ce06f5f837d6b9f2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752020"
---
# <a name="compiler-error-c2844"></a>Error del compilador C2844

' Member ': no puede ser un miembro de la interfaz ' interface '

Una [clase de interfaz](../../extensions/interface-class-cpp-component-extensions.md) no puede contener un miembro de datos a menos que sea también una propiedad.

No se permite ningún elemento que no sea una función de propiedad o miembro en una interfaz. Además, no se permiten constructores, destructores ni operadores.

En el ejemplo siguiente se genera C2844:

```cpp
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
