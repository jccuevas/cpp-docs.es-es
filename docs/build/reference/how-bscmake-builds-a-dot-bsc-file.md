---
title: "C&#243;mo compila BSCMAKE un archivo .Bsc | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de información de examen (.bsc), compilar"
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C&#243;mo compila BSCMAKE un archivo .Bsc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

BSCMAKE compila o recompila un archivo .bsc de la forma más eficaz posible.  Para evitar posibles problemas, es importante comprender el proceso de compilación.  
  
 Cuando BSCMAKE compila un archivo de información de examen, trunca los archivos .sbr a longitud cero.  Durante una compilación posterior del mismo archivo, un archivo .sbr de longitud cero \(o vacío\) indica a BSCMAKE que el archivo .sbr no tiene una contribución nueva que aportar.  Esta indicación pone en conocimiento de BSCMAKE que no es necesaria una actualización de esa parte del archivo y basta con una compilación incremental.  En todas las compilaciones \(a menos que se especifique la opción \/n\), BSCMAKE intenta primero actualizar el archivo de forma incremental usando sólo los archivos .sbr que han cambiado.  
  
 BSCMAKE busca un archivo .bsc que tenga el nombre especificado con la opción \/o.  Si no se especifica \/o, BSCMAKE busca un archivo con el nombre base del primer archivo .sbr y una extensión .bsc.  Si el archivo existe, BSCMAKE realiza una compilación incremental del archivo de información de examen usando solo los archivos .sbr participantes.  Si el archivo no existe, BSCMAKE realiza una compilación completa usando todos los archivos .sbr.  A continuación se exponen las reglas correspondientes a compilaciones:  
  
-   Para que una compilación completa se realice correctamente, todos los archivos .sbr especificados deben existir y no haber sido truncados.  Si se ha truncado un archivo .sbr, se debe recompilar \(mediante una recompilación o ensamblado\) antes de ejecutar BSCMAKE.  
  
-   Para que una compilación incremental se realice correctamente, debe existir el archivo .bsc.  Todos los archivos .sbr participantes, incluso los archivos vacíos, deben existir y especificarse en la línea de comandos de BSCMAKE.  Si se omite un archivo .sbr de la línea de comandos, BSCMAKE quita su contribución del archivo.  
  
## Vea también  
 [Crear un archivo .Bsc](../../build/reference/building-a-dot-bsc-file.md)