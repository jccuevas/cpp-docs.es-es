---
title: "Error del compilador C3728 | Microsoft Docs"
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
  - "C3728"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3728"
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3728
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'evento': el evento no tiene un método raise  
  
 Se han incluido, mediante la directiva [\#using](../../preprocessor/hash-using-directive-cpp.md), metadatos creados con un lenguaje, como C\#, que no permite provocar un evento desde fuera de la clase en la que se definió; además, un programa de Visual C\+\+ que usa programación CLR ha intentado provocar el evento.  
  
 Para provocar un evento en un programa desarrollado en un lenguaje como C\#, la clase que contiene el evento tiene que definir también un método público que provoque el evento.