---
title: Error grave de NMAKE U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 33be3312e1f0aaa7f1e8aad64b44ea9aefd25346
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182843"
---
# <a name="nmake-fatal-error-u1059"></a>Error grave de NMAKE U1059

> error de sintaxis: falta '} ' en dependiente

Se especificó incorrectamente una ruta de búsqueda para un dependiente. Se ha omitido un espacio en la ruta de acceso o la llave de cierre ( **}** ).

La sintaxis de una especificación de directorio para un dependiente es

> **{** *directorios* **} dependiente**

donde *directorios* especifica una o más rutas de acceso, separadas por un punto y coma ( **;** ). No se permiten espacios.

Si una de las rutas de acceso de una parte o de una ruta de búsqueda se ha reemplazado por una macro, asegúrese de que no existan espacios en la expansión de macro.
