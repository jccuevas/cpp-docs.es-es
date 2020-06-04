---
title: Advertencia del compilador C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: 091d988a5af277e78a2954eb5b0b95bc64c56069
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165267"
---
# <a name="compiler-warning-c4430"></a>Advertencia del compilador C4430

falta el especificador de tipo; se presupone int. Nota: C++ no admite default-int

Este error se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2005: todas las declaraciones deben especificar explícitamente el tipo; int ya no se supone.

C4430 siempre se emite como un error.  Puede desactivar esta advertencia con el `#pragma warning` o **/WD**; vea [Warning](../../preprocessor/warning.md) o [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/wo,/WV,/WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4430.

```cpp
// C4430.cpp
// compile with: /c
struct CMyClass {
   CUndeclared m_myClass;  // C4430
   int m_myClass;  // OK
};

typedef struct {
   POINT();   // C4430
   // try the following line instead
   // int POINT();
   unsigned x;
   unsigned y;
} POINT;
```
