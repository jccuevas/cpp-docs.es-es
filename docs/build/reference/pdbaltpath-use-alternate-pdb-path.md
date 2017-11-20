---
title: -PDBALTPATH (Usar ruta de PDB alternativa) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /pdbaltpath
dev_langs: C++
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a35e83f28a78acf199e74118cc1fef359666cf1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (usar ruta de PDB alternativa)
```  
/PDBALTPATH:pdb_file_name  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *pdb_file_name*  
 La ruta de acceso y el nombre del archivo .pdb.  
  
## <a name="remarks"></a>Comentarios  
 Utilice esta opción si quiere ofrecer una ubicación alternativa para el archivo de base de datos de programa (.pdb) en un archivo binario compilado. Normalmente, el enlazador registra la ubicación del archivo .pdb en los archivos binarios que produce. Puede utilizar esta opción si quiere proporcionar otra ruta de acceso y otro nombre de archivo para el archivo .pdb. La información que se indica con /PDBALTPATH no cambia la ubicación ni el nombre del archivo .pdb en sí: cambia la información que escribe el enlazador en el archivo binario. Así, puede indicar una ruta de acceso que sea independiente de la estructura de archivos del equipo donde se realiza la compilación. Dos usos habituales de esta opción consisten en proporcionar una ruta de acceso de red o un archivo sin información de ruta de acceso.  
  
 El valor de *pdb_file_name* puede ser una cadena arbitraria, una variable de entorno o **% _PDB %**. El enlazador expandirá una variable de entorno, como **% SystemRoot %**, a su valor. El vinculador define las variables de entorno **% _PDB %** y **% _EXT %**. **% _PDB %** se expande al nombre de archivo del archivo .pdb real sin información de ruta de acceso y **% _EXT %** es la extensión del ejecutable generado.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)   
 [/PDBPATH](../../build/reference/pdbpath.md)