---
title: "Advertencia del compilador (nivel 4) C4220 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4220"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4220"
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 4) C4220
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

varargs coincide con los parámetros restantes  
  
 Con las extensiones de Microsoft habilitadas \(\/Ze\), un puntero a una función coincide con un puntero a una función que posee argumentos similares pero variables.  
  
## Ejemplo  
  
```  
// C4220.c  
// compile with: /W4  
  
int ( *pFunc1) ( int a, ... );  
int ( *pFunc2) ( int a, int b);  
  
int main()  
{  
   if ( pFunc1 != pFunc2 ) {};  // C4220  
}  
```  
  
 Tales punteros no coinciden cuando se habilita la compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\).