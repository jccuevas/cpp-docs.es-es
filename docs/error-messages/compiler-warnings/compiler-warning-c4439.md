---
title: Advertencia del compilador C4439 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4439
dev_langs:
- C++
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 646b057f3f25bec8b686b08d50f0e473542ddcfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076117"
---
# <a name="compiler-warning-c4439"></a>Advertencia del compilador C4439

'function': definición de función con un tipo administrado en la firma debe tener una convención de llamada __clrcall

El compilador lo reemplazó implícitamente una convención de llamada con [__clrcall](../../cpp/clrcall.md). Para resolver esta advertencia, quite el `__cdecl` o `__stdcall` convención de llamada.

C4439 siempre se emite como un error. Puede desactivar esta advertencia con el `#pragma warning` o **/wd**; vea [advertencia](../../preprocessor/warning.md) o  [ /w, / W0, / W1, / W2, / w3, / W4, / W1, / W2, / w3, / W4, / Wall, / WD, / we, / WO, / wv, /WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md)para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4439.

```
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```