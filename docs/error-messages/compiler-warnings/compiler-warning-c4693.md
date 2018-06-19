---
title: Advertencia del compilador C4693 | Documentos de Microsoft
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4693
dev_langs:
- C++
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8230e60d65c80b4f839cc8a1c97ccc0c7b18086
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273886"
---
# <a name="compiler-warning-c4693"></a>Advertencia del compilador C4693

> 'class': una clase abstracta sealed no puede tener miembros de instancia 'Test'

Si un tipo se marca [sellado](../../windows/sealed-cpp-component-extensions.md) y [abstracta](../../windows/abstract-cpp-component-extensions.md), sólo puede tener miembros estáticos.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, utilice [#pragma warning](../../preprocessor/warning.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4693.

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```