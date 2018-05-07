---
title: Advertencia del compilador C4957 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4957
dev_langs:
- C++
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a76fb6ff4c00317da3e65c5bf31979c777ea51e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4957"></a>Advertencia del compilador C4957
'cast': la conversión explícita de 'cast_from' a 'cast_to' no es comprobable  
  
 Una conversión producirá una imagen no comprobable.  
  
 Algunas conversiones son seguras (por ejemplo, un elemento `static_cast` que desencadena conversiones definidas por el usuario y un elemento `const_cast`). Se garantiza que un elemento [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) genera código comprobable.  
  
 Para obtener más información, consulte [código puro y comprobable (C++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 Esta advertencia se emite como un error y puede deshabilitarse con pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .  
  
 El ejemplo siguiente genera la advertencia C4957:  
  
```  
// C4957.cpp  
// compile with: /clr:safe  
// #pragma warning( disable : 4957 )  
using namespace System;  
int main() {  
   Object ^ o = "Hello, World!";  
   String ^ s = static_cast<String^>(o);   // C4957  
   String ^ s2 = safe_cast<String^>(o);   // OK  
}  
```