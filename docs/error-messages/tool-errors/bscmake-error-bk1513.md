---
title: Error de BSCMAKE BK1513 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93664a1224b85ec808805da0172aec408e875bc9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295745"
---
# <a name="bscmake-error-bk1513"></a>Error de BSCMAKE BK1513
la actualización no incremental requiere todos los archivos .SBR  
  
 BSCMAKE no puede compilar un archivo nuevo de información de examen (.bsc) debido a que uno o más archivos .sbr están truncados. Para buscar los nombres de los archivos .sbr truncados, lea la [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) advertencias que acompañan a este error.  
  
 BSCMAKE puede actualizar un archivo .bsc con un archivo .sbr truncado, pero no puede compilar uno nuevo. BSCMAKE podría compilar un archivo .bsc nuevo por las siguientes razones:  
  
-   Falta el archivo. bsc.  
  
-   Se ha especificado un nombre de archivo incorrecto para el archivo .bsc.  
  
-   El archivo .bsc está dañado.  
  
 Para resolver este problema, elimine los archivos .sbr truncados y recompílelos, o limpie la solución y recompílela. (En el IDE, elija **generar**, **Limpiar solución**y, a continuación, elija **generar**, **volver a generar solución**.)