---
title: "Compiler Error C3209 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3209"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3209"
ms.assetid: 1de44e39-69d1-4894-8f89-ff92136e8e5d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Compiler Error C3209
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': la clase genérica debe ser una clase administrada o WinRT  
  
 Una clase genérica debe ser una clase administrada o una clase de Windows en tiempo de ejecución.  
  
 En el siguiente ejemplo se genera el error C3209 y se muestra cómo corregirlo:  
  
```  
// C3209.cpp  
// compile with: /clr  
generic <class T>  
class C {};   // C3209  
  
// OK - ref class can be generic  
generic <class T>  
ref class D {};  
```