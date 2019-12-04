---
title: Error del compilador C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 7315dad7959cdd3b950ed814b13be3867399d332
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761821"
---
# <a name="compiler-error-c3161"></a>Error del compilador C3161

' interfaz ': la clase anidada, estructura, Unión o interfaz en una interfaz no es válida; la interfaz de anidamiento en una clase, struct o Union no es válida

Un [__interface](../../cpp/interface.md) solo puede aparecer en el ámbito global o dentro de un espacio de nombres. Una clase, estructura o Unión no puede aparecer en una interfaz.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3161.

```cpp
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```
