---
title: "Error irrecuperable C1311 | Microsoft Docs"
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
  - "C1311"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1311"
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1311
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El formato COFF no puede inicializar estáticamente 'var' con \<número\> bytes de una dirección  
  
 Una dirección cuyo valor no se conoce en tiempo de compilación no se puede asignar de forma estática a una variable cuyo tipo tenga una capacidad de almacenamiento inferior a cuatro bytes.  
  
 Este error puede aparecer en código que, en otras circunstancias, sería código de C\+\+ válido.  
  
 El ejemplo siguiente muestra una condición que podría producir el error C1311.  
  
```  
char c = (char)"Hello, world";   // C1311  
char *d = (char*)"Hello, world";   // OK  
```