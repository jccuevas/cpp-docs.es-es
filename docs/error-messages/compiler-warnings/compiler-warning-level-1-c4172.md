---
title: "Advertencia del compilador (nivel 1) C4172 | Microsoft Docs"
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
  - "C4172"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4172"
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4172
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

devolución de dirección de la variable local o temporal  
  
 Una función devuelve la dirección de una variable local u objeto temporal.  Las variables locales y objetos temporales se destruyen cuando una función devuelve su valor, por lo que la dirección devuelta no es válida.  
  
 Vuelva a diseñar la función para que no devuelva la dirección de un objeto local.  
  
 El código siguiente genera el error C4172:  
  
```  
// C4172.cpp  
// compile with: /W1 /LD  
float f = 10;  
  
const double& bar() {  
// try the following line instead  
// const float& bar() {  
   return f;   // C4172  
}  
```