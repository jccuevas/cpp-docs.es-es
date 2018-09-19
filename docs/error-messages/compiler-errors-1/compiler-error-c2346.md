---
title: Error del compilador C2346 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec916bcdce1a43c597d8cfae10e5393cbeb99ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108619"
---
# <a name="compiler-error-c2346"></a>Error del compilador C2346

'function' no se puede compilar como nativa: razón

El compilador no pudo compilar una función en MSIL.

Para obtener más información, consulte [managed, unmanaged](../../preprocessor/managed-unmanaged.md) y [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Para corregir este error

1. Quite el código en la función que no se puede compilar en MSIL.

1. Cualquiera que no compile el módulo con **/CLR**, o marque la función como no administrados con el pragma no administrada.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2346.

```
// C2346.cpp
// processor: x86
// compile with: /clr
// C2346 expected
struct S
{
   S()
   {
      { __asm { nop } }
   }
   virtual __clrcall ~S() { }
};

void main()
{
   S s;
}
```