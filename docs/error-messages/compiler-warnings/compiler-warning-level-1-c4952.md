---
title: "Advertencia del compilador (nivel 1) C4952 | Microsoft Docs"
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
  - "C4952"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4952"
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4952
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': no se encuentran datos de perfil en la base de datos del programa 'archivo\_pgd'  
  
 Al usar [\/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después `/LTCG:PGINSTRUMENT` y que tiene presente una nueva función \(***function***\).  
  
 La advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.  
  
 Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE`.