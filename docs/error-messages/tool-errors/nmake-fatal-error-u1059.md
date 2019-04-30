---
title: Error grave de NMAKE U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 3c148bf2feb7ba12686e00b29f5bf90cb9f2f2d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367296"
---
# <a name="nmake-fatal-error-u1059"></a>Error grave de NMAKE U1059

> error de sintaxis: '}' no se encuentra en dependiente

Se especificó incorrectamente una ruta de acceso de búsqueda para un dependiente. Existe un espacio en la ruta de acceso o la llave de cierre (**}**) se ha omitido.

La sintaxis de una especificación de directorio para un dependiente es

> **{** *directorios* **} dependientes**

donde *directorios* especifica uno o más rutas de acceso, separadas por punto y coma (**;**). No se permiten espacios.

Si la totalidad o parte de una ruta de búsqueda se sustituye por una macro, asegúrese de que no existen espacios en blanco en la expansión de macro.