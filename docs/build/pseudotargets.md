---
title: Pseudodestinos
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
ms.openlocfilehash: 34b2b2f0d54a6e11bdfd6e818eb08d01721d80e2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414850"
---
# <a name="pseudotargets"></a>Pseudodestinos

Un pseudodestino es una etiqueta que se usa en lugar de un nombre de archivo en una línea de dependencia. Se interpreta como un archivo que no existe y, por lo que no está actualizada. NMAKE supone que la marca de tiempo de un pseudodestino es la más reciente de todos sus elementos dependientes. Si no tiene dependientes, se supone que la hora actual. Si un pseudodestino se usa como destino, siempre se ejecutan sus comandos. Un pseudodestino utilizado como dependiente debe aparecer también como un destino en otra dependencia. Sin embargo, esa dependencia no necesita tener un bloque de comandos.

Nombres de pseudodestinos siguen las reglas de sintaxis de nombre de archivo para los destinos. Sin embargo, si el nombre no tiene una extensión (es decir, no tiene un período), se puede superar el límite de 8 caracteres para los nombres de archivo y puede tener hasta 256 caracteres.

## <a name="see-also"></a>Vea también

[Destinos](../build/targets.md)
