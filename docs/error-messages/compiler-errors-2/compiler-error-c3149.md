---
title: "Error del compilador C3149 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3149"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3149"
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3149
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : no utilice este tipo aquí sin un 'char' de nivel superior  
  
 No se especificó correctamente una declaración.  
  
 Por ejemplo, tal vez ha definido un tipo CLR en el ámbito global e intenta crear una variable del tipo como parte de la definición.  Como no se permiten variables globales de tipos CLR, el compilador genera el error C3149.  
  
 Para solucionarlo, declare las variables de tipos CLR dentro de una función o definición de tipo.  
  
 El código siguiente genera el error C3149:  
  
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
  
 El código siguiente genera el error C3149:  
  
```  
// C3149b.cpp  
// compile with: /clr /c  
delegate int MyDelegate(const int, int);  
void Test1(MyDelegate m) {}   // C3149  
void Test2(MyDelegate ^ m) {}   // OK  
```  
  
 **Extensiones administradas de C\+\+**  
  
 No se utilizó correctamente un objeto administrado.  
  
 El código siguiente genera el error C3149:  
  
```  
// C3149c.cpp  
// compile with: /clr:oldSyntax  
__gc class A {};  
  
int main() {  
   A a = new A;   // C3149  
   A *a = new A;   // OK  
}  
```