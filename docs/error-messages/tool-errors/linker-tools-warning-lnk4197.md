---
title: Las herramientas del vinculador LNK4197 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4197
dev_langs:
- C++
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfef7f0fe2d9cd50fa6a18ad682c3e4d80df99c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300844"
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