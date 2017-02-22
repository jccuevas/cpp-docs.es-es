---
title: "Advertencia del compilador (nivel 1) C4829 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4829"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4829"
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# Advertencia del compilador (nivel 1) C4829
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Parámetros posiblemente incorrectos para la función main.Considere 'int main\(Platform::Array\<Platform::String^\>^ argv\)'  
  
 Algunas funciones, como main, no pueden tomar parámetros de tipo de referencia.  La compilación se realizará correctamente, pero la imagen resultante probablemente no se ejecutará.  
  
 El siguiente ejemplo genera el error C4829:  
  
```  
// C4829.cpp  
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp  
int main(Platform::String ^ s) {}   // C4829  
  
```