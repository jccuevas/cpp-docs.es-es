---
title: "Advertencia PRJ0041 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0041"
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia PRJ0041 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede encontrar la dependencia 'dependencia' que falta para el archivo 'archivo'.El proyecto aún puede compilarse, pero puede que continúe pareciendo obsoleto hasta que se encuentre este archivo.  
  
 Un archivo \(de recursos, .odl o .idl\) contiene una instrucción include que el sistema del proyecto no puede resolver.  
  
 Dado que el sistema del proyecto no procesa las instrucciones del preprocesador \(por ejemplo, \#if\), es posible que la instrucción que genera el error no forme parte realmente de la compilación.  
  
 Parra corregir esta advertencia, elimine todo el código que no sea necesario en los archivos .rc o agregue archivos de marcadores de posición con el nombre adecuado.