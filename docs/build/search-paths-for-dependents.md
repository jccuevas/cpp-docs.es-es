---
title: Rutas de búsqueda para dependientes
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: 8856d845d51072d205c84278978c7fbb447aed9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448807"
---
# <a name="search-paths-for-dependents"></a>Rutas de búsqueda para dependientes

Cada dependiente tiene una ruta de acceso de búsqueda opcional, especificar como sigue:

## <a name="syntax"></a>Sintaxis

```
{directory[;directory...]}dependent
```

## <a name="remarks"></a>Comentarios

NMAKE busca una dependencia en primer lugar en el directorio actual y, a continuación, en los directorios en el orden especificado. Parte o la totalidad de una ruta de búsqueda, puede especificar una macro. Los nombres de directorio encerrarlo entre llaves ({}); Separe varios directorios con punto y coma (;). No se permiten espacios o tabulaciones.

## <a name="see-also"></a>Vea también

[Dependientes](../build/dependents.md)