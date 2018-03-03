---
title: Las herramientas del vinculador LNK1106 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1106
dev_langs:
- C++
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 793d788462a3a449c654c30ec874399a3bb85728
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1106"></a>Error de las herramientas del vinculador LNK1106
archivo no válido o disco lleno: no se puede buscar en ubicación  
  
 La herramienta no pudo leer o escribir en `location` en un archivo asignado a memoria.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Disco está lleno.  
  
     Libere espacio y volver a vincular.  
  
2.  Intentar vincular a través de una red.  
  
     Algunas redes no son totalmente compatibles con los archivos asignados a memoria utilizados por el vinculador. Intente vincular en el disco local.  
  
3.  Bloque no válido en el disco.  
  
     Aunque el sistema operativo y el hardware del disco deben ha detectado un error de este tipo, puede que desee ejecutar un programa de comprobación de disco.  
  
4.  Espacio de montón.  
  
     Vea [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) para obtener más información.