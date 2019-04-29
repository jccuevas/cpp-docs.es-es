---
title: Rutas de búsqueda para dependientes
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: bc2c430c43f408065234c9df50977003eafd3cb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318308"
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

[Dependientes](dependents.md)
