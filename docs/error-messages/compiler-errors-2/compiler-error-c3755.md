---
title: Error del compilador C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 0150693ae84b45dc62c11cfdc59369eb25a819cd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757285"
---
# <a name="compiler-error-c3755"></a>Error del compilador C3755

' delegado ': no se puede definir un delegado

Un [delegado (C++ extensiones de componentes)](../../extensions/delegate-cpp-component-extensions.md) se puede declarar pero no definir.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3755.

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>Ejemplo

C3755 también puede producirse si intenta crear una plantilla de delegado. En el ejemplo siguiente se genera C3755.

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
