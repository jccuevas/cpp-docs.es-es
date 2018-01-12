---
title: Las herramientas del vinculador LNK4197 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4197
dev_langs: C++
helpviewer_keywords: LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1fadbf2ba5b18004f0e89142c88a68437842a92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4197"></a>Advertencia de las herramientas del vinculador LNK4197
exportar 'nombredeexportación' varias veces; usará la primera especificación  
  
 Se especificó una exportación en varios y de maneras diferentes. El vinculador usa la primera especificación y omite el resto.  
  
 Si va a reconstruir la biblioteca de tiempo de ejecución de C, puede omitir este mensaje.  
  
 Si se especifica una exportación exactamente del mismo modo varias veces, el vinculador no emitirá una advertencia.  
  
 Por ejemplo, el siguiente contenido de un archivo .def provocaría esta advertencia:  
  
```  
EXPORTS  
   functioname      NONAME  
   functioname      @10  
```  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  La misma exportación se especifica en la línea de comandos (a través de exportación:) y en el archivo .def  
  
2.  La misma exportación aparece dos veces en el archivo .def con diferentes atributos.