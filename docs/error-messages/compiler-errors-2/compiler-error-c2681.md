---
title: "Error del compilador C2681 | Microsoft Docs"
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
  - "C2681"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2681"
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2681
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : tipo de expresión no válida para nombre  
  
 Un operador de conversión intentó realizar una conversión desde un tipo no válido.  Por ejemplo, si se utiliza el operador [dynamic\_cast](../../cpp/dynamic-cast-operator.md) para convertir una expresión a un tipo de puntero, la expresión de origen debe ser un puntero.  
  
 El código siguiente genera el error C2681:  
  
```  
// C2681.cpp  
class A { virtual void f(); };  
  
void g(int i) {  
    A* pa;  
    pa = dynamic_cast<A*>(i);  // C2681  
}  
```