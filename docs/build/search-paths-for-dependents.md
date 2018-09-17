---
title: Rutas de búsqueda para dependientes | Microsoft Docs
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
ms.openlocfilehash: d1fd407f99abb98fb949b6d5bcc45b10c6ff9121
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706319"
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