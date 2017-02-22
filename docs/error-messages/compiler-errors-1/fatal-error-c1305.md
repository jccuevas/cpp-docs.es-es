---
title: "Error irrecuperable C1305 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1305"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1305"
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error irrecuperable C1305
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la base de datos del perfil 'archivo\_pgd' es para una arquitectura diferente  
  
 Se ha pasado a [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) un archivo .pgd generado a partir de la operación \/LTCG:PGINSTRUMENT de otra plataforma.  Las [optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md) están disponibles para las plataformas x86 y [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)].  Sin embargo, un archivo .pgd generado con una operación \/LTCG:PGINSTRUMENT de una plataforma no es válido como entrada para una operación \/LTCG:PGOPTIMIZE de otra plataforma.  
  
 Para resolver este error, pase únicamente un archivo .pgd creado mediante las operaciones \/LTCG:PGINSTRUMENT a \/LTCG:PGOPTIMIZE de la misma plataforma.