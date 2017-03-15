---
title: "Error PRJ0031 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0031"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0031"
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error PRJ0031 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La propiedad 'Resultados' del paso de compilación personalizada correspondiente al archivo 'archivo' contenía 'macro' que se evalúa como 'expansión\_de\_macro'.  
  
 Un paso de compilación personalizada de un archivo presentó un resultado erróneo debido a un problema de evaluación de macro.  Este error también puede deberse a que la ruta de acceso esté mal construida, con caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso del archivo.  
  
 Para resolver este error, corrija la macro o la especificación de ruta.  La ruta evaluada es una ruta absoluta del directorio de proyecto.