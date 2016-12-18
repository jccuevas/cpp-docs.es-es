---
title: "Error PRJ0008 al compilar el proyecto | Microsoft Docs"
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
  - "PRJ0008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0008"
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error PRJ0008 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede eliminar el archivo 'nombre\_archivo'.  
  
 **Compruebe que el archivo no está abierto en otro proceso y que no está protegido contra escritura.**  
  
 Al recompilar o al limpiar, Visual C\+\+ elimina todos los archivos intermedios y archivos de salida utilizados para compilar, así como los archivos que satisfagan las especificaciones de comodines establecidas en la propiedad **Extensiones para eliminar al limpiar** de la [página de propiedades Valores de configuración](../../ide/general-property-page-project.md).  
  
 Verá este error si Visual C\+\+ no puede eliminar un archivo.  Para solucionarlo, convierta en grabable el archivo y el directorio que lo contiene para el usuario que va a compilar.