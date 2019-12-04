---
title: Error del compilador C3807
ms.date: 11/04/2016
f1_keywords:
- C3807
helpviewer_keywords:
- C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
ms.openlocfilehash: a4b33782c0a1e5abb811210c9e7a28da7040c805
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755270"
---
# <a name="compiler-error-c3807"></a>Error del compilador C3807

' type ': una clase con el atributo ComImport no puede derivar de ' tipo2 ', solo se permite la implementación de la interfaz

Un tipo que se deriva de <xref:System.Runtime.InteropServices.ComImportAttribute> solo puede implementar una interfaz.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3807.

```cpp
// C3807.cpp
// compile with: /clr /c
ref struct S {};
interface struct I {};

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 : S {};   // C3807
ref struct S2 : I {};
```
