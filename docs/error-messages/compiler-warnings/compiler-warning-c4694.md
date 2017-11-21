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
ms.openlocfilehash: 1af20859e394fe62403358107b74f9d1df5facb1
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2017
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