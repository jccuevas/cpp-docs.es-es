---
title: "Error del compilador C2692 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2692"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2692"
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error del compilador C2692
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre\_de\_función' : se requieren funciones que se ajusten completamente al prototipo en el compilador C con la opción '\/clr'  
  
 Al compilar para el código administrado de .NET, el compilador de C requiere declaraciones de función ANSI.  Asimismo, si una función no acepta parámetros, debe declarar explícitamente `void` como tipo de parámetro.