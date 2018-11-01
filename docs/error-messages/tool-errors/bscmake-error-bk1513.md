---
title: Error de BSCMAKE BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: c02e9b47b3d32e4d21914188b96913d6dff03127
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477225"
---
# <a name="bscmake-error-bk1513"></a>Error de BSCMAKE BK1513

la actualización no incremental requiere todos los archivos .SBR

BSCMAKE no puede compilar un archivo nuevo de información de examen (.bsc) debido a que uno o más archivos .sbr están truncados. Para obtener los nombres de los archivos .sbr truncados, lea el [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) advertencias que acompañan a este error.

BSCMAKE puede actualizar un archivo .bsc con un archivo .sbr truncado, pero no puede compilar uno nuevo. BSCMAKE podría compilar un archivo .bsc nuevo por las siguientes razones:

- Falta el archivo. bsc.

- Se ha especificado un nombre de archivo incorrecto para el archivo .bsc.

- El archivo .bsc está dañado.

Para resolver este problema, elimine los archivos .sbr truncados y recompílelos, o limpie la solución y recompílela. (En el IDE, elija **compilar**, **Limpiar solución**y, a continuación, elija **compilar**, **recompilar solución**.)