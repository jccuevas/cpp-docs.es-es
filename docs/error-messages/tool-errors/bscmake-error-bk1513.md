---
title: Error de BSCMAKE BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: 3a16163f33814be18a67833995362ee9b13d8118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197644"
---
# <a name="bscmake-error-bk1513"></a>Error de BSCMAKE BK1513

la actualización no incremental requiere todos los archivos .SBR

BSCMAKE no puede compilar un archivo nuevo de información de examen (.bsc) debido a que uno o más archivos .sbr están truncados. Para buscar los nombres de los archivos. SBR truncados, lea las advertencias de [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) que acompañan a este error.

BSCMAKE puede actualizar un archivo .bsc con un archivo .sbr truncado, pero no puede compilar uno nuevo. BSCMAKE podría compilar un archivo .bsc nuevo por las siguientes razones:

- Falta el archivo. bsc.

- Se ha especificado un nombre de archivo incorrecto para el archivo .bsc.

- El archivo .bsc está dañado.

Para resolver este problema, elimine los archivos .sbr truncados y recompílelos, o limpie la solución y recompílela. (En el IDE, elija **compilar**, **limpiar solución**y, a continuación, elija **compilar**, **recompilar solución**).
