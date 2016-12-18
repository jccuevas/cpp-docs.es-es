---
title: "Controlar los mensajes reflejados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "control de mensajes, mensajes reflejados"
  - "mensajes reflejados, controlar"
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controlar los mensajes reflejados
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La reflexión de mensaje permite controlar los mensajes para un control, como `WM_CTLCOLOR`, **WM\_COMMAND**, y **WM\_NOTIFY**, dentro del propio control.  Esto hace que el control más autónomo y portátil.  El mecanismo funciona con controles comunes de Windows así como con controles ActiveX \(antes denominados controles OLE\).  
  
 La reflexión de mensaje permite reutilizar `CWnd`\- clases derivadas más fácilmente.  La reflexión de mensaje funciona mediante [CWnd::OnChildNotify](../Topic/CWnd::OnChildNotify.md), utilizando entradas especiales del mapa de mensajes de **ON\_XXX\_REFLECT** : por ejemplo, **ON\_CTLCOLOR\_REFLECT** y **ON\_CONTROL\_REFLECT**.  [Nota técnica 62](../mfc/tn062-message-reflection-for-windows-controls.md) explica la reflexión de mensaje con más detalle.  
  
## ¿Qué desea hacer?  
  
-   [Obtenga más información sobre la reflexión de mensaje](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [Implemente la reflexión de mensaje para un control común](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [Implemente la reflexión de mensaje para un control ActiveX](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)  
  
## Vea también  
 [Declarar funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)