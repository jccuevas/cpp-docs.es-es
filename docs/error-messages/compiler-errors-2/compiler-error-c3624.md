---
title: Error del compilador C3624
ms.date: 11/04/2016
f1_keywords:
- C3624
helpviewer_keywords:
- C3624
ms.assetid: eaac6a4f-eb11-4e4d-ab12-124ba995c5cf
ms.openlocfilehash: bb574b194f01aa1da27b962ed6be327f4f988c3c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563532"
---
# <a name="compiler-error-c3624"></a>Error del compilador C3624

'type': uso de este tipo requiere una referencia al ensamblado 'ensamblado'

No se especificó un ensamblado (referencia) necesario para compilar el código; pase el ensamblado a la [#using](../../preprocessor/hash-using-directive-cpp.md) directiva.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3624:

```
// C3624.cpp
// compile with: /clr /c
#using <System.Windows.Forms.dll>

// Uncomment the following 2 lines to resolve.
// #using <System.dll>
// #using <System.Drawing.dll>

using namespace System;

public ref class MyForm : public Windows::Forms::Form {};   // C3624
```
