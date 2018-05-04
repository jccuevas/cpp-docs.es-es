---
title: Rutas de búsqueda para dependientes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 577fc7e44bfff35cf7efdcff20dc4cdca1c7001e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="search-paths-for-dependents"></a>Rutas de búsqueda para dependientes
Cada dependiente tiene una ruta de acceso de búsqueda opcional, especificar como sigue:  
  
## <a name="syntax"></a>Sintaxis  
  
```  
{directory[;directory...]}dependent  
```  
  
## <a name="remarks"></a>Comentarios  
 NMAKE busca una dependencia en primer lugar en el directorio actual y, a continuación, en directorios en el orden especificado. Una macro puede especificar parte o la totalidad de una ruta de acceso de búsqueda. Incluya los nombres de directorio entre llaves ({}); Separe varios directorios con un punto y coma (;). No se permiten espacios ni tabulaciones.  
  
## <a name="see-also"></a>Vea también  
 [Dependientes](../build/dependents.md)