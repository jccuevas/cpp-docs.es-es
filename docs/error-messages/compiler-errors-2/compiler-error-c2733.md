---
title: "Error del compilador C2733 | Microsoft Docs"
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
  - "C2733"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2733"
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2733
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se permite una segunda vinculación C de la función sobrecargada 'función'  
  
 Se ha declarado más de una función sobrecargada con vinculación C.  Al utilizar la vinculación de C, sólo una forma de una función especificada puede ser externa.  Dado que las funciones sobrecargadas tienen el mismo nombre no decorado, no se pueden utilizar con programas de C.  
  
 El código siguiente genera el error C2733:  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```