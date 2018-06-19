---
title: Múltiples archivos en línea | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee9be15f029c0aaab3ca4bc47fb183e1499c2e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368218"
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