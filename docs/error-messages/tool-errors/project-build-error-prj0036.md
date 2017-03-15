---
title: "Error PRJ0036 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0036"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0036"
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error PRJ0036 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La propiedad 'Archivos adicionales' de la herramienta de implementación Web contenía una entrada no válida.  
  
 La propiedad Archivos adicionales de la página de propiedades Implementación Web contenía un error, posiblemente debido a un problema de evaluación de macro.  Este error también puede deberse a que la ruta de acceso esté mal construida, con caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso del archivo.  
  
 Para resolver este error, corrija la macro o la especificación de ruta.  La ruta evaluada es una ruta absoluta del directorio de proyecto.  
  
 Este error también podría deberse a que uno de los archivos a los que se hace referencia no existe.