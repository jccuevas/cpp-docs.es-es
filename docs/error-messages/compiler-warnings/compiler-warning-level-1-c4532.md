---
title: "Advertencia del compilador (nivel 1) C4532 | Microsoft Docs"
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
  - "C4532"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4532"
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4532
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'continue' : al saltar desde el bloque \_\_finally\/finally se produce un comportamiento no definido durante el control de finalización  
  
 El compilador encontró una de las siguientes palabras clave:  
  
-   [continue](../../cpp/continue-statement-cpp.md)  
  
-   [break](../../cpp/break-statement-cpp.md)  
  
-   [goto](../../cpp/goto-statement-cpp.md)  
  
 causando un salto fuera de un bloque [\_\_finally](../../cpp/try-finally-statement.md) o [finally](../../dotnet/finally.md) durante una terminación anormal.  
  
 Si se produce una excepción mientras se está desenredando la pila, durante la ejecución de los controladores de terminación \(los bloques `__finally` o finally\), y el código salta fuera de un bloque `__finally` antes de que éste finalice, el comportamiento será indefinido.  El control no puede regresar al código de desenredo, por lo que no es posible controlar la excepción adecuadamente.  
  
 Si se desea saltar fuera de un bloque **\_\_finally**, se debe comprobar antes si existe terminación anormal.  
  
 El ejemplo siguiente genera la advertencia C4532; basta con convertir en comentario las instrucciones de salto para resolver las advertencias.  
  
```  
// C4532.cpp  
// compile with: /W1  
// C4532 expected  
int main() {  
   int i;  
   for (i = 0; i < 10; i++) {  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         continue;  
      }  
  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         break;  
      }  
   }  
}  
```