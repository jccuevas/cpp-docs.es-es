---
title: "Enlaces de notificaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "carga retrasada de archivos DLL, enlaces de notificación"
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Enlaces de notificaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se llama a los enlaces de notificación inmediatamente antes de que se realicen las acciones siguientes en la rutina auxiliar:  
  
-   Comprobar si ya se ha cargado el identificador almacenado para la biblioteca.  
  
-   Llamar a **LoadLibrary** para intentar la carga de la DLL.  
  
-   Llamar a **GetProcAddress** para intentar conseguir la dirección del procedimiento.  
  
-   Volver al *thunk* de importación de carga retrasada.  
  
 El enlace de notificación se habilita:  
  
-   Si se proporciona una nueva definición del puntero **\_\_pfnDliNotifyHook2** que se inicializa para apuntar a nuestra propia función, la cual recibe las notificaciones.  
  
     O bien  
  
-   Si se establece el puntero **\_\_pfnDliNotifyHook2** en la función de enlace antes de que se efectúen llamadas a la DLL cuya carga está retrasando el programa.  
  
 Si la notificación es **dliStartProcessing**, la función de enlace puede devolver:  
  
 NULL  
 La rutina auxiliar predeterminada controla la carga de la DLL.  Sólo es de utilidad si la llamada tiene fines informativos.  
  
 puntero a función  
 Se omite el control de carga retrasada predeterminado.  Esto permite proporcionar un controlador de carga propio.  
  
 Si la notificación es **dliNotePreLoadLibrary**, la función de enlace puede devolver:  
  
-   0, si sólo se desean notificaciones informativas.  
  
-   HMODULE para la DLL cargada, si HMODULE la ha cargado.  
  
 Si la notificación es **dliNotePreGetProcAddress**, la función de enlace puede devolver:  
  
-   0, si sólo se desean notificaciones informativas.  
  
-   La dirección de la función importada, si la función de enlace obtiene la propia dirección.  
  
 Si la notificación es **dliNoteEndProcessing**, el valor devuelto de la función de enlace se omite.  
  
 Si se inicializa este puntero \(valor distinto de cero\), la rutina auxiliar de carga retrasada llamará a la función en determinados puntos de notificación durante su ejecución.  El puntero a función tiene la siguiente definición:  
  
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
  
 Las notificaciones pasan una estructura **DelayLoadInfo** a la función de enlace junto con el valor de notificación.  Estos datos son idénticos a los usados por la rutina auxiliar de carga retrasada.  El valor de notificación será uno de los valores definidos en [Definiciones de estructura y de constante](../../build/reference/structure-and-constant-definitions.md).  
  
## Vea también  
 [Notificación y control de errores](../../build/reference/error-handling-and-notification.md)