---
title: "UI Support Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.ui"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces de usuario, clases ATL"
  - "interfaces de usuario, support classes"
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# UI Support Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases siguientes proporcionan compatibilidad general de la interfaz de usuario:  
  
-   [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) una interfaz a Microsoft HTML que analiza y que muestra el motor.  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) proporciona los métodos de la entidad de seguridad que un contenedor se comunica con un control.  administra la activación y la desactivación de controles en contexto.  
  
-   [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md) administra la reactivación de controles en contexto.  Permite a un control sin ventana recibir mensajes, así como para participar en operaciones de arrastrar y colocar.  
  
-   Comunicación de[IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md) Assists entre un control en contexto y su contenedor.  
  
-   [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md) permite a un control para mostrarse directamente y notificar al contenedor de cambios en la pantalla.  Proporciona compatibilidad para el gráfico libre de centelleo, los controles no rectangulares y transparentes, y pruebas de posicionamiento.  
  
## artículos relacionados  
 [tutorial de ATL](../atl/active-template-library-atl-tutorial.md)  
  
## Vea también  
 [Class Overview](../atl/atl-class-overview.md)