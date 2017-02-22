---
title: "Error irrecuperable C1099 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1099"
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error irrecuperable C1099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El motor de la función Editar y continuar está deteniendo la compilación  
  
 Editar y continuar cargó un archivo de encabezado precompilado al preparar la compilación de cambios en el código, pero las acciones posteriores \(como los cambios en el código antes de la instrucción `#include` del encabezado precompilado o la detención del depurador\) impidieron que Editar y continuar finalizase la compilación con ese proceso. No es necesario realizar ninguna acción para corregir este error.