---
title: "Error PRJ0032 al compilar el proyecto | Microsoft Docs"
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
  - "PRJ0032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0032"
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error PRJ0032 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La propiedad 'Outputs' del paso de compilación personalizada del nivel de proyecto contenía 'macro', que evalúa en 'expansión\_de\_macro'.  
  
 Un paso de compilación personalizada de un proyecto presentó un resultado erróneo debido probablemente a un problema de evaluación de macro.  Este error también puede deberse a que la ruta de acceso esté mal construida, con caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso del archivo.  
  
 Para resolver este error, corrija la macro o la especificación de ruta.  La ruta evaluada es una ruta absoluta del directorio de proyecto.