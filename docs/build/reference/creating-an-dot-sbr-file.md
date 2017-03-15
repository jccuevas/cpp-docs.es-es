---
title: "Crear un archivo .Sbr | Microsoft Docs"
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
  - ".sbr (archivos)"
  - "BSCMAKE, archivos de entrada"
  - "símbolos locales en la información de examen"
  - "SBR (archivos)"
  - "archivos del explorador de código fuente"
  - "símbolos"
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Crear un archivo .Sbr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los archivos de entrada para BSCMAKE son archivos .sbr.  El compilador crea un archivo .sbr para cada archivo objeto \(.obj\) que compila.  Cuando se compila o se actualiza un archivo de información de examen, todos los archivos .sbr del proyecto deben estar disponibles en disco.  
  
 Para crear un archivo .sbr con toda la información posible, se ha de especificar [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).  
  
 Para crear un archivo .sbr que no contenga símbolos locales, se ha de especificar [\/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md).  Si los archivos .sbr contienen símbolos locales, se pueden omitir en el archivo .bsc mediante la [opción \/El](../../build/reference/bscmake-options.md)`.` de BSCMAKE.  
  
 Se puede crear un archivo .sbr sin realizar una compilación completa.  Por ejemplo, se puede especificar la opción \/Zs en el compilador para realizar una comprobación de sintaxis y generar un archivo .sbr si se especifica \/FR o \/Fr.  
  
 El proceso de compilación puede ser más eficaz si los archivos .sbr se empaquetan antes para quitar las definiciones sin referencia.  El compilador empaqueta automáticamente los archivos .sbr.  
  
## Vea también  
 [Crear un archivo .Bsc](../../build/reference/building-a-dot-bsc-file.md)