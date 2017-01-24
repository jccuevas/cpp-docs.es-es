---
title: "Compiler Error C2396 | Microsoft Docs"
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
  - "C2396"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2396"
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C2396
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'your\_type::operator'type'' : función de conversión CLR o WinRT definida por el usuario no válida.Debe convertir de o a: 'T^', 'T^%', 'T^&', donde T \= 'your\_type'  
  
 Una función de conversión en un tipo administrado o de Windows en tiempo de ejecución no tenía al menos un parámetro con un tipo igual al tipo que contiene la función de conversión.  
  
 El siguiente ejemplo genera el error C2396 y muestra cómo corregirlo:  
  
```  
// C2396.cpp  
// compile with: /clr /c  
  
ref struct Y {  
   static operator int(char c);   // C2396  
  
   // OK  
   static operator int(Y^ hY);  
   // or  
   static operator Y^(char c);  
};  
```