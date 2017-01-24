---
title: "/PDBPATH | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/pdbpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb (archivos), ruta de acceso"
  - "/PDBPATH (opción de dumpbin)"
  - "PDB (archivos), ruta de acceso"
  - "PDBPATH (opción de dumpbin)"
  - "-PDBPATH (opción de dumpbin)"
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /PDBPATH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDBPATH[:VERBOSE] filename  
```  
  
## Comentarios  
 donde:  
  
 *filename*  
 Es el nombre del archivo .dll o .exe para el que desea buscar el archivo .pdb correspondiente.  
  
 VERBOSE \(opcional\)  
 Notifica todos los directorios donde se buscó el archivo .pdb.  
  
## Comentarios  
 \/PDBPATH buscará en las mismas rutas del equipo en que buscaría el depurador un archivo .pdb y notificará qué archivos .pdb \(si existen\) se corresponden con el archivo especificado en *filename*.  
  
 Al utilizar el depurador de Visual Studio podría producirse algún problema si éste utiliza un archivo .pdb correspondiente a una versión diferente del archivo que se está depurando.  
  
 \/PDBPATH buscará archivos .pdb en las siguientes rutas:  
  
-   La ubicación en la que reside el ejecutable.  
  
-   La ubicación del archivo PDB insertado en el ejecutable.  Suele ser la ubicación en la que se realizó la vinculación de la imagen.  
  
-   La ruta de búsqueda configurada en el entorno de desarrollo integrado de Visual Studio.  
  
-   Las rutas de las variables de entorno \_NT\_SYMBOL\_PATH y \_NT\_ALT\_SYMBOL\_PATH.  
  
-   El directorio de Windows.  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)   
 [\/PDBALTPATH \(usar ruta de PDB alternativa\)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)