---
title: Rutas de búsqueda para dependientes
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: 9f2251a5fff9d708a783797d04606572e5ebce62
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426464"
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
