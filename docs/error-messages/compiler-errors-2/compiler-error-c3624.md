---
title: Error del compilador C3624
ms.date: 11/04/2016
f1_keywords:
- C3624
helpviewer_keywords:
- C3624
ms.assetid: eaac6a4f-eb11-4e4d-ab12-124ba995c5cf
ms.openlocfilehash: 3b4f71ed71ddb1b14ed51ccbcd420284ddcc70f6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761925"
---
# <a name="compiler-error-c3624"></a>Error del compilador C3624

' type ': el uso de este tipo requiere una referencia al ensamblado ' Assembly '

No se especificó un ensamblado (referencia) necesario para compilar el código; Pase el ensamblado a la directiva [#using](../../preprocessor/hash-using-directive-cpp.md) .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3624:

```cpp
// C3624.cpp
// compile with: /clr /c
#using <System.Windows.Forms.dll>

// Uncomment the following 2 lines to resolve.
// #using <System.dll>
// #using <System.Drawing.dll>

using namespace System;

public ref class MyForm : public Windows::Forms::Form {};   // C3624
```
