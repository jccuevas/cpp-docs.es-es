---
title: "Servidores de automatizaci&#243;n: Problemas de duraci&#243;n de objetos | Microsoft Docs"
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
  - "servidores de automatización, duración de los objetos"
  - "duración, servidor de automatización"
  - "objetos [C++], duración"
  - "servidores, duración de automatización"
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Servidores de automatizaci&#243;n: Problemas de duraci&#243;n de objetos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando un cliente de automatización crea o genera un elemento OLE, el servidor pasa al cliente un puntero a ese objeto.  El cliente establece una referencia al objeto con una llamada a la función OLE [IUnknown::AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379).  Esta referencia está en vigor hasta que el cliente llame a [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317). \(Las aplicaciones cliente escritas con clases OLE de la biblioteca Microsoft Foundation Class no necesitan realizar estas llamadas; el marco lo hace.\) El sistema OLE y el propio servidor pueden establecer referencias al objeto.  Un servidor no debe destruir un objeto mientras mantiene las referencias externas al objeto en vigor.  
  
 El marco mantiene un recuento interno del número de referencias a los objetos de servidor derivado de [CCmdTarget](../mfc/reference/ccmdtarget-class.md).  Se actualiza este recuento cuando el cliente de automatización u otra entidad agrega o libere una referencia al objeto.  
  
 Cuando el recuento de referencias se convierte en 0, el marco de trabajo llama a la función virtual [CCmdTarget::OnFinalRelease](../Topic/CCmdTarget::OnFinalRelease.md).  La implementación predeterminada de este llamadas de función el operador de **borrar** para eliminar este objeto.  
  
 La biblioteca Microsoft Foundation Class ofrece funciones adicionales para controlar el comportamiento de aplicación cuando los clientes externos tienen referencias a objetos de la aplicación.  Además de mantener el recuento de referencias a cada objeto, los servidores mantienen un recuento global de objetos activos.  Las funciones globales [AfxOleLockApp](../Topic/AfxOleLockApp.md) y [AfxOleUnlockApp](../Topic/AfxOleUnlockApp.md) actualizan el recuento de la aplicación de objetos activos.  Si este número es cero, la aplicación no termina cuando el usuario elige cierre de menú sistema o a la salida del menú archivo.  En su lugar, se oculta la ventana principal de la aplicación \(pero no destruido\) hasta que se hayan completado todas las solicitudes pendientes de cliente.  Normalmente, `AfxOleLockApp` y `AfxOleUnlockApp` se denominan en los constructores y destructores, respectivamente, clases esa automatización admiten.  
  
 Las circunstancias convierten a veces el servidor para finalizar mientras que un cliente todavía tiene una referencia a un objeto.  Por ejemplo, depende de un recurso en el que el servidor puede volverse no disponible, haciendo que el servidor encuentra un error.  El usuario también puede cerrar un documento de servidor que contiene los objetos a los que otras aplicaciones tienen referencias.  
  
 En [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)], vea `IUnknown::AddRef` y `IUnknown::Release`.  
  
## Vea también  
 [Servidores de automatización](../mfc/automation-servers.md)   
 [AfxOleCanExitApp](../Topic/AfxOleCanExitApp.md)