---
title: "Error de las herramientas del vinculador LNK2011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2011"
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de las herramientas del vinculador LNK2011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

objeto precompilado no vinculado; quizá la imagen no se pueda ejecutar  
  
 Si se usan encabezados precompilados, LINK necesita que se vinculen todos los archivos objeto creados con dichos encabezados.  Si se dispone de un archivo de código fuente que se usa para generar un encabezado precompilado que se va a utilizar con otros archivos de código fuente, ahora hay que incluir el archivo objeto creado junto con el encabezado precompilado.  
  
 Por ejemplo, si se compila un archivo con el nombre STUB.cpp para crear un encabezado precompilado para su uso con otros archivos de código, se debe vincular con STUB.obj o se obtendrá este error.  En las siguientes líneas de comandos, la línea uno se usa para crear un encabezado precompilado, COMMON.pch, que se utiliza junto con PROG1.cpp y PROG2.cpp en las líneas dos y tres.  El archivo STUB.cpp sólo contiene líneas `#include` \(las mismas líneas `#include` que en PROG1.cpp y PROG2.cpp\) y solamente se emplea para generar encabezados precompilados.  En la última línea, STUB.obj debe estar vinculado para evitar LNK2011.  
  
```  
cl /c /Yccommon.h stub.cpp  
cl /c /Yucommon.h prog1.cpp  
cl /c /Yucommon.h prog2.cpp  
link /out:prog.exe stub.obj prog1.obj prog2.obj  
```