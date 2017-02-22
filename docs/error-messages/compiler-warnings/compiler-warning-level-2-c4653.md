---
title: "Advertencia del compilador (nivel 2) C4653 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4653"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4653"
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 2) C4653
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la opción del compilador 'opción' no es coherente con el encabezado precompilado; se ha omitido la opción de la línea de comandos actual  
  
 Una opción especificada con la opción Utilizar encabezado precompilado \([\/Yu](../../build/reference/yu-use-precompiled-header-file.md)\) era incoherente con las opciones especificadas al crear el encabezado precompilado.  Esta compilación utilizó las opciones especificadas cuando se creó el encabezado precompilado.  
  
 Esta advertencia puede producirse cuando se especifica un valor diferente para la opción Empaquetar estructuras \([\/Zp](../../build/reference/zp-struct-member-alignment.md)\) durante la compilación del encabezado precompilado.