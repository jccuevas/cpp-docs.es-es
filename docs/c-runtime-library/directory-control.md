---
title: Control de directorio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.programs
dev_langs: C++
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4674029fe5bdfc4323f580fcc0567b2ceeb1929
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="directory-control"></a>Control de directorio
Estas rutinas tienen acceso a información sobre la estructura de directorios, la modifican y la obtienen.  
  
### <a name="directory-control-routines"></a>Rutinas de directorio  
  
|Rutina|Usar|  
|-------------|---------|  
|[_chdir, _wchdir](../c-runtime-library/reference/chdir-wchdir.md)|Cambia el directorio de trabajo actual.|  
|[_chdrive](../c-runtime-library/reference/chdrive.md)|Cambia la unidad actual.|  
|[_getcwd, _wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|Obtiene el directorio de trabajo actual para la unidad predeterminada.|  
|[_getdcwd, _wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|Obtiene el directorio de trabajo actual para la unidad especificada.|  
|[_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|Completa una estructura `_diskfree_t` con información sobre una unidad de disco.|  
|[_getdrive](../c-runtime-library/reference/getdrive.md)|Obtiene la unidad (predeterminada) actual.|  
|[_getdrives](../c-runtime-library/reference/getdrives.md)|Devuelve una máscara de bits que representa las unidades de disco disponibles actualmente.|  
|[_mkdir, _wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|Crea un nuevo directorio.|  
|[_rmdir, _wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|Quitar directorio|  
|[_searchenv, _wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md), [_searchenv_s, _wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|Busca un archivo determinado en rutas de acceso especificadas.|  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [Control de archivos](../c-runtime-library/file-handling.md)   
 [Llamadas del sistema](../c-runtime-library/system-calls.md)