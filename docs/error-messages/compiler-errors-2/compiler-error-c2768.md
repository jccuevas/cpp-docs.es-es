---
title: "Error del compilador C2768 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2768"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2768"
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2768
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : uso no válido de los argumentos de plantilla explícitos  
  
 El compilador no ha podido determinar si la definición de una función era una especialización explícita de una plantilla de función o bien era para una nueva función.  
  
 Este error se ha introducido en Visual Studio .NET 2003 como parte de las mejoras de conformidad del compilador.  
  
 El código siguiente genera el error C2768:  
  
```  
// C2768.cpp  
template<typename T>  
void f(T) {}  
  
void f<int>(int) {}   // C2768  
  
// an explicit specialization  
template<>  
void f<int>(int) {}   
  
// global nontemplate function overload  
void f(int) {}  
```