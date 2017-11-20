---
title: "Rutas de búsqueda para dependientes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cf777c89c78ab844b61138c30a5a9a25ca6b91d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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