---
title: "Error del compilador C3552 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3552"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3552"
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3552
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'typename': un tipo de valor devuelto especificado en tiempo de ejecución no puede contener 'auto'  
  
 Si usa la palabra clave `auto` como marcador de posición del tipo de valor devuelto de una función, debe facilitar un tipo de valor devuelto especificado en tiempo de ejecución. Sin embargo, no puede usar otra palabra clave `auto` para especificar el tipo de valor devuelto especificado en tiempo de ejecución. Por ejemplo, el siguiente fragmento de código genera el error C3552.  
  
 `auto myFunction->auto; // C3552`