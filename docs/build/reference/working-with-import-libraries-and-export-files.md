---
title: "Trabajar con bibliotecas de importaci&#243;n y archivos de exportaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de exportación"
  - "bibliotecas de importación"
  - "bibliotecas de importación, crear"
  - "LIB [C++], /DEF (opción)"
  - "LIB [C++], bibliotecas de importación y archivos de exportación"
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Trabajar con bibliotecas de importaci&#243;n y archivos de exportaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede utilizar LIB con la opción \/DEF para crear una biblioteca de importación y un archivo de exportación.  LINK utiliza el archivo de exportación para compilar un programa que contiene exportaciones \(generalmente una biblioteca de vínculos dinámicos \(DLL\)\) y utiliza la biblioteca de importación para resolver referencias a dichas exportaciones en otros programas.  
  
 Observe que si crea la biblioteca de importación en un paso preliminar, antes de crear la .dll, debe pasar el mismo conjunto de archivos objeto cuando genere la .dll que cuando generó la biblioteca de importación.  
  
 En la mayoría de las situaciones no es necesario utilizar LIB para crear la biblioteca de importación.  Cuando vincule un programa \(un archivo ejecutable o uno DLL\) que contiene exportaciones, LINK crea automáticamente una biblioteca de importación que describe las exportaciones.  Posteriormente, cuando vincule un programa que haga referencia a las exportaciones, deberá especificar la biblioteca de importación.  
  
 Sin embargo, cuando un archivo DLL exporta a un programa desde el que también importa, de forma directa o indirecta, deberá utilizar LIB para crear una de las bibliotecas de importación.  Cuando LIB crea una biblioteca de importación, también crea un archivo de exportación.  Debe utilizar el archivo de exportación al vincular uno de los archivos DLL.  
  
## Vea también  
 [Referencia de LIB](../../build/reference/lib-reference.md)