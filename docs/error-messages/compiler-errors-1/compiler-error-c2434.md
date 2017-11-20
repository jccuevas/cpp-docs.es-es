---
title: Error del compilador C2434 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2434
dev_langs: C++
helpviewer_keywords: C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 954ef1f8db47c5cd9c420e8099cc3060ebb8a32b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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