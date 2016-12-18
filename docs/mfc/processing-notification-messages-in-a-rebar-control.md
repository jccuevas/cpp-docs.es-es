---
title: "Procesar mensajes de notificaci&#243;n en un control Rebar | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBarCtrl (clase), mensajes de notificación enviados por"
  - "notificaciones, CReBarCtrl"
  - "RBN_ (mensajes de notificación)"
  - "RBN_ (mensajes de notificación), descripción de"
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procesar mensajes de notificaci&#243;n en un control Rebar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En la clase principal del control rebar, cree una función de controlador de `OnChildNotify` con una instrucción switch para cualquier mensaje de notificación de rebar\- CONTROL \(`CReBarCtrl`\) que desea controlar.  Las notificaciones se envían a la ventana primaria cuando el usuario arrastra objetos sobre el control rebar, cambia el diseño de las bandas rebar, elimina bandas de control rebar, etc.  
  
 Los mensajes de notificación siguientes se pueden enviar por el objeto de control rebar:  
  
-   **RBN\_AUTOSIZE** Sent por un control rebar \(creado con el estilo de **RBS\_AUTOSIZE** \) cuando el rebar se ajusta automáticamente el tamaño.  
  
-   **RBN\_BEGINDRAG** Sent por un control rebar cuando el usuario comienza arrastrando una banda.  
  
-   **RBN\_CHILDSIZE** Sent por un control rebar cuando se cambia el tamaño de la ventana secundaria de una banda.  
  
-   **RBN\_DELETEDBAND** Sent por un control rebar una vez eliminado una banda.  
  
-   **RBN\_DELETINGBAND** Sent por un control rebar cuando una banda se va a eliminar.  
  
-   **RBN\_ENDDRAG** Sent por un control rebar cuando el usuario detiene el arrastrar de una banda.  
  
-   **RBN\_GETOBJECT** Sent por un control rebar \(creado con el estilo de **RBS\_REGISTERDROP** \) cuando se arrastra un objeto sobre una banda en el control.  
  
-   **RBN\_HEIGHTCHANGE** Sent por un control rebar cuando su alto ha cambiado.  
  
-   **RBN\_LAYOUTCHANGED** Sent por un control rebar cuando el usuario cambia el diseño de las bandas de control.  
  
 Para obtener más información sobre estas notificaciones, vea [Referencia de Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774375) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)