---
title: Compilador advertencia (nivel 4) C4242 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4242
dev_langs: C++
helpviewer_keywords: C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bee4a165ae59bd21491fdecfc8c25d18477d7c36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4242"></a>Advertencia del compilador (nivel 4) C4242
'identificador': conversión de 'tipo1' a 'tipo2', posible pérdida de datos  
  
 Los tipos son diferentes. Conversión de tipos puede producir pérdida de datos. El compilador realiza la conversión de tipos.  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 Para obtener más información sobre C4242, consulte [errores comunes del compilador](http://msdn.microsoft.com/library/windows/desktop/aa384160).  
  
 El ejemplo siguiente genera C4242:  
  
```  
// C4242.cpp  
// compile with: /W4  
#pragma warning(4:4242)  
int func() {  
   return 0;  
}  
  
int main() {  
   char a;  
   a = func();   // C4242, return type and variable type do not match  
}  
```