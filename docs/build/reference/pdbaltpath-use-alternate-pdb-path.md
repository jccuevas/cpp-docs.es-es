---
title: "/PDBALTPATH (usar ruta de PDB alternativa) | Microsoft Docs"
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
  - "/pdbaltpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb (archivos), ruta de acceso"
  - "/PDBALTPATH (opción de dumpbin)"
  - "PDB (archivos), ruta de acceso"
  - "PDBALTPATH (opción de dumpbin)"
  - "-PDBALTPATH (opción de dumpbin)"
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /PDBALTPATH (usar ruta de PDB alternativa)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDBALTPATH:pdb_file_name  
```  
  
## Comentarios  
 donde:  
  
 *pdb\_file\_name*  
 La ruta de acceso y el nombre del archivo .pdb.  
  
## Comentarios  
 Utilice esta opción si quiere ofrecer una ubicación alternativa para el archivo de base de datos de programa \(.pdb\) en un archivo binario compilado.  Normalmente, el enlazador registra la ubicación del archivo .pdb en los archivos binarios que produce.  Puede utilizar esta opción si quiere proporcionar otra ruta de acceso y otro nombre de archivo para el archivo .pdb.  La información que se indica con \/PDBALTPATH no cambia la ubicación ni el nombre del archivo .pdb en sí: cambia la información que escribe el enlazador en el archivo binario.  Así, puede indicar una ruta de acceso que sea independiente de la estructura de archivos del equipo donde se realiza la compilación.  Dos usos habituales de esta opción consisten en proporcionar una ruta de acceso de red o un archivo sin información de ruta de acceso.  
  
 El valor de *pdb\_file\_name* puede ser una cadena arbitraria, una variable de entorno o **%\_PDB%**.  El enlazador expandirá una variable de entorno, como **%SystemRoot%**, a su valor.  El enlazador define las variables de entorno **%\_PDB%** y **%\_EXT%**.  **%\_PDB%** se expande al nombre de archivo del archivo .pdb real sin información de ruta de acceso, y **%\_EXT%** es la extensión del ejecutable generado.  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)   
 [\/PDBPATH](../../build/reference/pdbpath.md)