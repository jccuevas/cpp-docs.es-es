---
title: "Múltiples archivos en línea | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 412c68f4d1279fea7969b3ddfdd2bf82e3cdbc47
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="multiple-inline-files"></a>Múltiples archivos en línea
Un comando puede crear más de un archivo en línea.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      command << <<  
inlinetext  
<<[KEEP | NOKEEP]  
inlinetext  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>Comentarios  
 Para cada archivo, especifique una o más líneas de texto insertado seguido por una línea de cierre que contiene el delimitador. Comience el texto del segundo archivo en la línea siguiente a la línea delimitadora para el primer archivo.  
  
## <a name="see-also"></a>Vea también  
 [Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)