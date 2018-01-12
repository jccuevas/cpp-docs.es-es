---
title: "Enlaces de notificación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 31490e3bb591af6568ffecddf68219c89a25e055
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="notification-hooks"></a>Enlaces de notificación
Los enlaces de notificación se llama justo antes de que se realizan las acciones siguientes en la rutina auxiliar:  
  
-   El identificador almacenado para la biblioteca se comprueba para ver si ya se ha cargado.  
  
-   **LoadLibrary** se llama para tratar la carga del archivo DLL.  
  
-   **GetProcAddress** se llama para intentar obtener la dirección del procedimiento.  
  
-   Volver al thunk de importación de carga de retraso.  
  
 Se habilita el enlace de notificación:  
  
-   Si se suministra una nueva definición del puntero **__pfnDliNotifyHook2** que se inicializa para que señale a su propia función que recibe las notificaciones.  
  
     O bien  
  
-   Al establecer el puntero **__pfnDliNotifyHook2** a la función de enlace antes de que todas las llamadas a la DLL que el programa retrasar la carga.  
  
 Si la notificación es **dliStartProcessing**, la función de enlace puede devolver:  
  
 NULL  
 La rutina auxiliar predeterminada controla la carga del archivo DLL. Esto es útil para llamar solo con fines informativos.  
  
 Puntero a función  
 Omitir el control de carga retrasada predeterminado. Esto le permite proporcionar su propio controlador de carga.  
  
 Si la notificación es **dliNotePreLoadLibrary**, la función de enlace puede devolver:  
  
-   0, si solo se desean notificaciones informativas.  
  
-   HMODULE para la DLL cargada, si el propio archivo DLL cargado.  
  
 Si la notificación es **dliNotePreGetProcAddress**, la función de enlace puede devolver:  
  
-   0, si solo se desean notificaciones informativas.  
  
-   Dirección de la función importada, si la función de enlace obtiene la propia dirección.  
  
 Si la notificación es **dliNoteEndProcessing**, se omite el valor devuelto de la función de enlace.  
  
 Si se inicializa este puntero (valor distinto de cero), la aplicación auxiliar de carga de retraso invocará la función en determinados puntos de notificación durante su ejecución. El puntero de función tiene la siguiente definición:  
  
```  
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