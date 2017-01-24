---
title: "Advertencia del compilador (nivel 2) C4244 | Microsoft Docs"
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
  - "C4244"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4244"
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 2) C4244
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'argumento' : conversión de 'tipo1' a 'tipo2', posible pérdida de datos  
  
 Un tipo de punto flotante se ha convertido en un tipo entero.  Puede haberse producido una pérdida de datos.  
  
 Si recibe el error C4244, debería cambiar el programa y utilizar tipos compatibles, o agregar cierta lógica al código y asegurarse de que el intervalo de valores posibles sea siempre compatible con los tipos que utiliza.  
  
 La advertencia C4244 también puede producirse en los niveles 3 y 4; vea [Advertencia del compilador \(nivels 3 and 4\) C4244](../Topic/Compiler%20Warning%20\(levels%203%20and%204\)%20C4244.md) para obtener más información.  
  
## Ejemplo  
 El código siguiente genera el error C4244:  
  
```  
// C4244_level2.cpp  
// compile with: /W2  
  
int f(int x){ return 0; }  
int main() {  
   double x = 10.1;  
   int i = 10;  
   return (f(x));   // C4244  
   // try the following line instead  
   // return (f(i));  
}  
```