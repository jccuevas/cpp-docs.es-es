---
title: "Controles Rich Edit sin l&#237;mite | Microsoft Docs"
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
  - "controles Rich Edit sin límite"
  - "CRichEditCtrl (clase), sin límite"
  - "controles Rich Edit, sin límite"
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Controles Rich Edit sin l&#237;mite
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La aplicación puede cambiar el tamaño de un control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) como sea necesario para que siempre el mismo tamaño que su contenido.  Un control rich edit admite esta supuesta funcionalidad “insondable” enviar su ventana primaria un mensaje de notificación de [EN\_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983) siempre que el tamaño de su contenido cambia.  
  
 Al procesar el mensaje de notificación de **EN\_REQUESTRESIZE** , una aplicación debe cambiar el tamaño del control a las dimensiones de la estructura especificada de [REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950) .  Una aplicación también puede mover cualquier información sobre de controles para incluir el cambio de control de alto.  Para cambiar el tamaño del control, puede utilizar la función [SetWindowPos](../Topic/CWnd::SetWindowPos.md)de `CWnd` .  
  
 Puede forzar un control rich edit insondable para enviar un mensaje de notificación de **EN\_REQUESTRESIZE** utilizando la función miembro de [RequestResize](../Topic/CRichEditCtrl::RequestResize.md) .  Este mensaje puede ser útil en el controlador de [OnSize](../Topic/CWnd::OnSize.md) .  
  
 Para recibir los mensajes de notificación de **EN\_REQUESTRESIZE** , debe habilitar la notificación utilizando la función miembro de `SetEventMask` .  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)