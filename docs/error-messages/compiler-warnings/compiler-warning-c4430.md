---
title: Advertencia del compilador C4430 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4430
dev_langs:
- C++
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79c0045b568a24ad6702e748e82a8ebd88c41044
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093927"
---
# <a name="compiler-warning-c4430"></a>Advertencia del compilador C4430

falta el especificador de tipo; se presupone int. Nota: C++ no admite default-int

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: todas las declaraciones deben especificar explícitamente el tipo; ya no se presupone int.

C4430 siempre se emite como un error.  Puede desactivar esta advertencia con el `#pragma warning` o **/wd**; vea [advertencia](../../preprocessor/warning.md) o  [ /w, / W0, / W1, / W2, / w3, / W4, / W1, / W2, / w3, / W4, / Wall, / WD, / we, / WO, / wv, /WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md)para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4430.

```
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