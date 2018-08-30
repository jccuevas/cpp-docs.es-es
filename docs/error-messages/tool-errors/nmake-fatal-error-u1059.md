---
title: Error grave de NMAKE U1059 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b54919398c757bfe05f747ff57341f31decfc61
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200795"
---
# <a name="nmake-fatal-error-u1059"></a>Error grave de NMAKE U1059

> error de sintaxis: '}' no se encuentra en dependiente

Se especificó incorrectamente una ruta de acceso de búsqueda para un dependiente. Existe un espacio en la ruta de acceso o la llave de cierre (**}**) se ha omitido.

La sintaxis de una especificación de directorio para un dependiente es

> **{** *directorios* **} dependientes**

donde *directorios* especifica uno o más rutas de acceso, separadas por punto y coma (**;**). No se permiten espacios.

Si la totalidad o parte de una ruta de búsqueda se sustituye por una macro, asegúrese de que no existen espacios en blanco en la expansión de macro.