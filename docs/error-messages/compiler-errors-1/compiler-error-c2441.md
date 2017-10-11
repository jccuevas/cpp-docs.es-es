---
title: Error del compilador C2441 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 6868feadda4c0c0f3d65a86c77a403b8965fded5
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2441"></a>Error del compilador C2441
'variable': un símbolo declarado con __declspec (proceso) debe ser constante en/CLR: pure modo  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
 De forma predeterminada, las variables son por dominio de aplicación bajo **/CLR: pure**. Una variable marcada `__declspec(process)` en **/CLR: pure** es propenso a errores si se modifica en un dominio de aplicación y leer en otro.  
  
 Por lo tanto, el compilador exige por proceso de ser variables `const` en **/CLR: puro**, hacer que ellos leen solo en todos los dominios de aplicación.  
  
 Para obtener más información, consulte [proceso](../../cpp/process.md) y [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2441.  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```
