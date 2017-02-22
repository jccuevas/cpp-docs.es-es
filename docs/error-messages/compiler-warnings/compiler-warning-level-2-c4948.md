---
title: "Advertencia del compilador (nivel 2) C4948 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4948"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4948"
ms.assetid: d006cb17-754a-4c70-ba7f-c3200e2cd8fa
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Advertencia del compilador (nivel 2) C4948
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el tipo de valor devuelto de 'descriptor de acceso' no coincide con el tipo del último parámetro de un establecedor correspondiente  
  
 El compilador ha detectado que los tipos de datos obtenidos y establecidos para una propiedad indizada no coinciden.  
  
 Sólo se puede reproducir el error C4948 utilizando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C4948:  
  
```  
// C4948.cpp  
// compile with: /clr:oldSyntax /LD /W2  
  
__gc class MyClass  
{  
   int prop __nogc [2];  
   public:  
  
      __property int get_P(int i)  
      // try the following line instead  
      // __property char get_P(int i)  
      {  
         return prop[i];  
      }  
  
      __property void set_P(int i, char c)  
      {  
         prop[i] = c;  
      }  
};   // C4948  
```