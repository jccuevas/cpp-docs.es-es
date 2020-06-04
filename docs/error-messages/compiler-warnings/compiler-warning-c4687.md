---
title: Advertencia del compilador C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 83f5c535f9cf252783110838c181c88c8b0096ee
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631610"
---
# <a name="compiler-warning-c4687"></a>Advertencia del compilador C4687

> '*Class*': una clase abstracta sellada no puede implementar una interfaz '*interface*'

## <a name="remarks"></a>Comentarios

Un tipo abstracto sellado normalmente solo es útil para mantener las funciones miembro estáticas.

Para obtener más información, vea [abstract](../../extensions/abstract-cpp-component-extensions.md) y [Sealed](../../extensions/sealed-cpp-component-extensions.md).

C4687 se emite como un error de forma predeterminada. Puede suprimir C4687 con la pragma [Warning](../../preprocessor/warning.md) . Si está seguro de que desea implementar una interfaz en un tipo abstracto sellado, puede suprimir C4687.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4687.

```cpp
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```
