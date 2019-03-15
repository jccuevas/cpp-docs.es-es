---
title: Enlaces de error
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
ms.openlocfilehash: 2fc22ae77d729868adbf8c37d40e450e35a8e866
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811997"
---
# <a name="failure-hooks"></a>Enlaces de error

El enlace de error está habilitado en la misma manera que el [enlace de notificación](notification-hooks.md). Puede seguir la rutina de enlace tiene que devolver un valor adecuado para que el procesamiento (HINSTANCE o FARPROC) o 0 para indicar que debe producirse una excepción.

La variable de puntero que hace referencia a la función definida por el usuario es:

```
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

El **DelayLoadInfo** estructura contiene todos los datos necesarios para generar informes precisos del error, incluido el valor de `GetLastError`.

Si la notificación es **dliFailLoadLib**, la función de enlace puede devolver:

- 0 si no puede controlar el error.

- HMODULE, si el enlace de error se ha corregido el problema y carga la propia biblioteca.

Si la notificación es **dliFailGetProc**, la función de enlace puede devolver:

- 0 si no puede controlar el error.

- Una dirección válida proc (dirección de función de importación), si el enlace de error se ha realizado correctamente al obtener la dirección propia.

## <a name="see-also"></a>Vea también

[Notificación y control de errores](error-handling-and-notification.md)
