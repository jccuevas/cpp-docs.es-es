---
title: "Advertencia del compilador (nivel 1) C4129 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4129"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4129"
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4129
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'carácter' : secuencia de escape de carácter no reconocida  
  
 El `character` que sigue a una barra diagonal inversa \(\\\) en una constante de caracteres o de cadena no se reconoce como secuencia de escape válida.  La barra diagonal inversa se omite y no se imprime.  El carácter que sigue a la barra diagonal inversa sí se imprime.  
  
 Para imprimir una barra diagonal inversa simple, especifique una doble barra diagonal inversa \(\\\\\).  
  
 El estándar de C\+\+, en la sección 2.13.2 trata las secuencias de escape.  
  
 El código siguiente genera el error C4129:  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```