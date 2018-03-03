---
title: -PDBPATH | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /pdbpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ccbcedbf9cdd376fa7d9bced5c9d49542cee9f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="pdbpath"></a>/PDBPATH
```  
/PDBPATH[:VERBOSE] filename  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *filename*  
 El nombre del archivo .dll o .exe para el que desea buscar el archivo .pdb correspondiente.  
  
 VERBOSE (opcional)  
 Notifica todos los directorios donde se realizó un intento para buscar el archivo PDB.  
  
## <a name="remarks"></a>Comentarios  
 /PDBPATH buscará en el equipo a lo largo de las mismas rutas de acceso que el depurador podría buscar un archivo .pdb y notificará que, si existe, los archivos .pdb se corresponden con el archivo especificado en *filename*.  
  
 Al utilizar al depurador de Visual Studio, puede experimentar un problema debido al hecho de que el depurador está usando un archivo .pdb con una versión diferente del archivo que se está depurando.  
  
 /PDBPATH buscará archivos .pdb en las rutas de acceso siguientes:  
  
-   Compruebe la ubicación donde reside el archivo ejecutable.  
  
-   Compruebe la ubicación del archivo PDB insertado en el archivo ejecutable. Esto suele ser la ubicación en el momento de que la imagen se vincula.  
  
-   Compruebe la ruta de búsqueda configurada en el IDE de Visual Studio.  
  
-   Comprobar a lo largo de las rutas de acceso en el _NT_SYMBOL_PATH y _NT_ALT_SYMBOL_PATH las variables de entorno.  
  
-   Compruebe en el directorio de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)   
 [/PDBALTPATH (Usar ruta de PDB alternativa)](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)