---
title: "Advertencia del compilador (nivel 1) C4010 | Microsoft Docs"
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
  - "C4010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4010"
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el comentario de una sola línea contiene un carácter de continuación de línea  
  
 Un comentario de una sola línea, que se inserta con \/\/, contiene una barra diagonal inversa \(\\\) que actúa como carácter de continuación de línea.  El compilador interpreta la siguiente línea como continuación y la trata como comentario.  
  
 Algunos editores orientados a la sintaxis no indican la línea que sigue al carácter de continuación como comentario.  Omita la codificación de color de la sintaxis en las líneas que causan esta advertencia.  
  
 El código siguiente genera el error C4010:  
  
```  
// C4010.cpp  
// compile with: /WX  
int main() {  
   // the next line is also a comment because of the backslash \  
   int a = 3; // C4010  
   a++;  
}  
```