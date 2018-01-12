---
title: Advertencia del compilador C4694 | Documentos de Microsoft
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: article
f1_keywords: C4694
dev_langs: C++
helpviewer_keywords: C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f635aad0039812b50bd48a36f307ab5f60cba10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4694"></a>Advertencia del compilador C4694

> '*clase*': una clase abstracta sealed no puede tener una clase base*clase_base*'

Una clase abstracta y sellada no puede heredar de un tipo de referencia. Una clase sellada y abstracta no puede implementar las funciones de clase base ni permitir que se use como clase base.

Para obtener más información, consulte [abstracta](../../windows/abstract-cpp-component-extensions.md), [sellado](../../windows/sealed-cpp-component-extensions.md), y [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md).

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, utilice [#pragma warning](../../preprocessor/warning.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```