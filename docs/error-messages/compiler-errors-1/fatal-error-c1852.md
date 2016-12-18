---
title: "Error irrecuperable C1852 | Microsoft Docs"
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
  - "C1852"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1852"
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1852
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'filename' no es un archivo de encabezado precompilado válido  
  
 El archivo no es un encabezado precompilado.  
  
### Posibles causas del error:  
  
1.  Archivo no válido especificado con **\/Yu** o **\#pragma hdrstop**.  
  
2.  El compilador supone una extensión de archivo .pch si no se especifica lo contrario.