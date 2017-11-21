---
title: Las herramientas del vinculador LNK1201 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1201
dev_langs: C++
helpviewer_keywords: LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 344f56eb3097bad447d9a0b12a0c5aac6f68b119
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1201"></a>Error de las herramientas del vinculador LNK1201
Error al escribir en la base de datos de programa 'nombredearchivo'; comprobar si hay suficiente espacio en disco, ruta de acceso no válida o no tiene suficientes privilegios  
  
 VÍNCULO no pudo escribir en la base de datos de programa (PDB) para el archivo de salida.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Archivo está dañado. Elimine el archivo PDB y vuelva a vincular.  
  
2.  No hay suficiente espacio en disco para escribir el archivo.  
  
3.  Unidad no está disponible, posiblemente debido a un problema de red.  
  
4.  El depurador está activo en el programa que desea vincular.  
  
5.  Espacio de montón.  Vea [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) para obtener más información.