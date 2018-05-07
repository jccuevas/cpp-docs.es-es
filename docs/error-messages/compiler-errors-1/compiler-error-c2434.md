---
title: Error del compilador C2434 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2434
dev_langs:
- C++
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 543884392698a7a713dbc4c0bfd10dd19fcb0b1c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2434"></a>Error del compilador C2434
'símbolo': un símbolo declarado con __declspec (proceso) no se puede inicializar dinámicamente en/CLR: pure modo  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
 No es posible inicializar dinámicamente una variable por proceso en **/CLR: pure**. Para obtener más información, consulte [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) y [proceso](../../cpp/process.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2434.  
  
```  
// C2434.cpp  
// compile with: /clr:pure /c  
int f() { return 0; }  
__declspec(process) int i = f();   // C2434  
__declspec(process) int i2 = 0;   // OK  
```