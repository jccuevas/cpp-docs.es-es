---
title: Enlaces de notificación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97e471e2de1ecb6ec6664658a2f1c5df09bc8079
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700627"
---
# <a name="notification-hooks"></a>Enlaces de notificación

Los enlaces de notificación se llaman justo antes de que se realizan las acciones siguientes en la rutina auxiliar:

- El identificador almacenado para la biblioteca se comprueba para ver si ya se ha cargado.

- **LoadLibrary** se llama para tratar la carga del archivo DLL.

- **GetProcAddress** se llama para intentar obtener la dirección del procedimiento.

- Volver al código thunk carga de importación de retraso.

Se habilita el enlace de notificación:

- Si se suministra una nueva definición del puntero **__pfnDliNotifyHook2** que se inicializa para que apunte a su propia función que recibe las notificaciones.

   \-o -

- Al establecer el puntero **__pfnDliNotifyHook2** a la función de enlace antes de que todas las llamadas a la DLL que el programa es retrasar la carga.

Si la notificación es **dliStartProcessing**, la función de enlace puede devolver:

- NULL

   La aplicación auxiliar de predeterminado controla la carga del archivo DLL. Esto es útil para llamarse solo con fines informativos.

- puntero a función

   Omitir el control de carga retrasada de forma predeterminada. Esto le permite proporcionar su propio controlador de carga.

Si la notificación es **dliNotePreLoadLibrary**, la función de enlace puede devolver:

- 0, si simplemente desea notificaciones informativas.

- HMODULE para la DLL cargada, si el propio archivo DLL cargado.

Si la notificación es **dliNotePreGetProcAddress**, la función de enlace puede devolver:

- 0, si simplemente desea notificaciones informativas.

- Dirección de la función importada, si la función de enlace obtiene la dirección propia.

Si la notificación es **dliNoteEndProcessing**, se omite el valor devuelto de la función de enlace.

Si este puntero se inicializa (distinto de cero), la aplicación auxiliar de carga de retraso invocará la función en determinados puntos de notificación a lo largo de su ejecución. El puntero de función tiene la siguiente definición:

```C
// The "notify hook" gets called for every call to the
// delay load helper.  This allows a user to hook every call and
// skip the delay load helper entirely.
//
// dliNotify == {
//  dliStartProcessing |
//  dliNotePreLoadLibrary  |
//  dliNotePreGetProc |
//  dliNoteEndProcessing}
//  on this call.
//
ExternC
PfnDliHook   __pfnDliNotifyHook2;

// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

Las notificaciones pasan una **DelayLoadInfo** estructura a la función de enlace junto con el valor de notificación. Estos datos son idénticos al utilizado por la rutina de aplicación auxiliar de carga retrasada. El valor de notificación será uno de los valores definidos en [definiciones de estructura y constante](../../build/reference/structure-and-constant-definitions.md).

## <a name="see-also"></a>Vea también

[Notificación y control de errores](../../build/reference/error-handling-and-notification.md)