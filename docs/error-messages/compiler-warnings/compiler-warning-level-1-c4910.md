---
title: "Advertencia del compilador (nivel 1) C4910 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4910"
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# Advertencia del compilador (nivel 1) C4910
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\<identifier\>': '\_\_declspec\(dllexport\)' y 'extern' son incompatibles en una creación de instancia explícita  
  
 Las dos palabras clave `__declspec(dllexport)` y `extern` modifican la creación de instancias de plantilla explícita denominada *\<identifier\>*. Sin embargo, estas palabras clave son mutuamente excluyentes. La palabra clave `__declspec(dllexport)` implica que se cree una instancia de la clase de plantilla, mientras que la palabra clave `extern` que no se creen automáticamente instancias de la clase de plantilla.  
  
## Vea también  
 [Creación de instancias explícita](../../cpp/explicit-instantiation.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)   
 [Reglas y limitaciones generales](../../cpp/general-rules-and-limitations.md)