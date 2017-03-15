---
title: "Error del compilador C3230 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3230"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3230"
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3230
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': el argumento de tipo de plantilla para 'plantilla' no puede contener un parámetro de tipo genérico: 'parámetro'  
  
 Las instancias de las plantillas se crean en tiempo de compilación, mientras que las instancias de los genéricos se crean en tiempo de ejecución. Por consiguiente, no es posible generar código genérico que pueda llamar a la plantilla, porque no se pueden crear instancias de la plantilla en tiempo de ejecución si finalmente se conoce el tipo genérico.  
  
 El ejemplo siguiente genera la advertencia C3230:  
  
```  
// C3230.cpp // compile with: /clr /LD template <class S> void f(S t); generic <class U> ref class C { void f1(U x) { f(x);   // C3230 } };  
```