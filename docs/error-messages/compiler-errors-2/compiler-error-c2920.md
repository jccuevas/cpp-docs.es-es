---
title: "Compiler Error C2920 | Microsoft Docs"
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
  - "C2920"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2920"
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C2920
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

nueva definición: 'class': ya se ha declarado una clase de plantilla o genérica como 'type'  
  
 Una clase genérica o de plantilla tiene varias declaraciones que no son equivalentes.  Para corregir este error, utilice nombres diferentes para los distintos tipos o quite la nueva definición del nombre de tipo.  
  
 El ejemplo siguiente genera el error C2920 y muestra cómo corregirlo:  
  
```  
// C2920.cpp  
// compile with: /c  
typedef int TC1;  
template <class T>   
struct TC1 {};   // C2920  
struct TC2 {};   // OK - fix by using a different name  
```  
  
 También se puede producir C2920 al utilizar genéricos:  
  
```  
// C2920b.cpp  
// compile with: /clr /c  
typedef int GC1;  
generic <class T>   
ref struct GC1 {};   // C2920  
ref struct GC2 {};   // OK - fix by using a different name  
  
```