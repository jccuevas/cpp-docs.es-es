---
title: Error del compilador C3149 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3149
dev_langs: C++
helpviewer_keywords: C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 154ae99c5e47438f6fca3b85ac8318c1b14f7a30
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3149"></a>Error del compilador C3149
'type': no se puede usar este tipo aquí sin un 'char' de nivel superior  
  
 Una declaración no se especificó correctamente.  
  
 Por ejemplo, puede haber definido un tipo CLR en el ámbito global e intentó crear una variable del tipo como parte de la definición. Dado que no se permiten variables globales de tipos CLR, el compilador genera el error C3149.  
  
 Para resolver este error, declare las variables de tipos CLR dentro de una definición de función o tipo.  
  
 El ejemplo siguiente genera el error C3149:  
  
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
  
 El ejemplo siguiente genera el error C3149:  
  
```  
// C3149b.cpp  
// compile with: /clr /c  
delegate int MyDelegate(const int, int);  
void Test1(MyDelegate m) {}   // C3149  
void Test2(MyDelegate ^ m) {}   // OK  
```  
