---
title: "Control Containment Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.controls.containment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control containment classes"
ms.assetid: e0812aee-c078-4ced-b967-247976552b9a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Control Containment Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases siguientes proporcionan compatibilidad de contención para hospedar los controles:  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) proporciona los métodos para manipular una ventana que hospeda un control ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) proporciona los métodos para manipular una ventana que hospeda un control ActiveX y también tiene compatibilidad para hospedar controles ActiveX con licencia.  
  
-   Llamada de[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) los métodos de esta interfaz para establecer propiedades de ambiente disponibles para un control hospedado.  
  
-   Llamada de[IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) los métodos de esta interfaz para crear y\/o para asociar un control a un objeto host, o para obtener una interfaz de un control de hospedado.  
  
## artículos relacionados  
 [Preguntas más frecuentes sobre la contención de controles ATL](../atl/atl-control-containment-faq.md)  
  
## Vea también  
 [Class Overview](../atl/atl-class-overview.md)