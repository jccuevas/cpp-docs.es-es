---
title: Enlaces de error
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
ms.openlocfilehash: 2cd691ed4514ac4073f90691ed731670fbd22477
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417949"
---
# <a name="failure-hooks"></a>Enlaces de error

El enlace de error está habilitado en la misma manera que el [enlace de notificación](../../build/reference/notification-hooks.md). Puede seguir la rutina de enlace tiene que devolver un valor adecuado para que el procesamiento (HINSTANCE o FARPROC) o 0 para indicar que debe producirse una excepción.

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

[Notificación y control de errores](../../build/reference/error-handling-and-notification.md)
