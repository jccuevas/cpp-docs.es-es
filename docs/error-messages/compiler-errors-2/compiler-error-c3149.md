---
title: Error de compilador Error C3149 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3149
dev_langs:
- C++
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 555b3a7ac8e0d1e5de8eacd763c9ee63101e5b78
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3149"></a>Error del compilador C3149
'tipo': no se puede usar este tipo aquí sin un 'char' de nivel superior  
  
 No se especificó correctamente una declaración.  
  
 Por ejemplo, puede tiene definido un tipo CLR en el ámbito global y ha intentado crear una variable del tipo como parte de la definición. Ya no se admiten variables globales de tipos CLR, el compilador genera el error C3149.  
  
 Para resolver este error, declare las variables de tipos CLR dentro de una definición de función o tipo.  
  
 En el ejemplo siguiente genera el error C3149:  
  
```  
// C3149.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   // declare an array of value types   
   array< Int32 ^> IntArray;   // C3149  
   array< Int32>^ IntArray2;   // OK  
}  
```  
  
 En el ejemplo siguiente genera el error C3149:  
  
```  
// C3149b.cpp  
// compile with: /clr /c  
delegate int MyDelegate(const int, int);  
void Test1(MyDelegate m) {}   // C3149  
void Test2(MyDelegate ^ m) {}   // OK  
```  

