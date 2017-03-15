---
title: "Error del compilador C2765 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2765"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2765"
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2765
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : una especialización explícita de una plantilla de función no puede tener ningún argumento predeterminado  
  
 No permiten argumentos predeterminados en una especialización explícita de una plantilla de función.  Para obtener más información, vea [Especialización explícita de plantillas de función](../../cpp/explicit-specialization-of-function-templates.md).  
  
 El código siguiente genera el error C2765:  
  
```  
// C2765.cpp  
template<class T> void f(T t) {};  
  
template<> void f<char>(char c = 'a') {}   // C2765  
// try the following line instead  
// template<> void f<char>(char c) {}  
```