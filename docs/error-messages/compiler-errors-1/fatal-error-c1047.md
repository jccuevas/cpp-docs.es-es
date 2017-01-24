---
title: "Error irrecuperable C1047 | Microsoft Docs"
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
  - "C1047"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1047"
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1047
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El objeto o el archivo de biblioteca 'file' se creó con un compilador anterior a otros objetos; recompile las bibliotecas y los objetos antiguos.  
  
 El error C1047 se produce cuando los archivos o bibliotecas de objeto compilados con **\/LTCG** están vinculados entre sí, pero donde se crean esos archivos o bibliotecas de objetos con versiones diferentes del conjunto de herramientas de Visual C\+\+.  
  
 Esto puede suceder si empieza a usar una nueva versión del compilador pero no realiza una recompilación limpia de las bibliotecas o los archivos de objetos existentes.  
  
 Para resolver el error C1047, recompile todos los archivos y bibliotecas de objetos.