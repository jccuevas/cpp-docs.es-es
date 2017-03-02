---
title: Compilador advertencia (nivel 4) C4255 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4255
dev_langs:
- C++
helpviewer_keywords:
- C4255
ms.assetid: 2087b635-4b4c-4182-8a01-c26770d2bb88
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 307b802e317ab36d2097453fe88f0e03046e0930
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-4-c4255"></a>Advertencia del compilador (nivel 4) C4255
'función': no se ha proporcionado un prototipo de función: convirtiendo '()' a '(void)'  
  
 El compilador no encontró una lista explícita de argumentos de una función. Esta advertencia es para el compilador de C solo.  
  
 De forma predeterminada, esta advertencia está desactivada. Consulte [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para obtener más información.  
  
 El ejemplo siguiente genera C4255:  
  
```  
// C4255.c  
// compile with: /W4 /WX  
#pragma warning (default : 4255)  
  
void f()  { // C4255  
// try the following line instead  
//void f(void) {  
}  
  
int main(int argc, char *argv[]) {  
   f();  
}  
```
