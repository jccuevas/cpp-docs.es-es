---
title: "Controls: General Support Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.controls"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles [ATL]"
  - "general support classes"
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Controls: General Support Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases siguientes proporcionan compatibilidad para general para los controles ATL:  
  
-   La aplicación auxiliar de[CComControl](../atl/reference/ccomcontrol-class.md) Consists De funciones y los miembros de datos que son esenciales para ATL controlan.  
  
-   [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) proporciona los métodos necesarios para los controles.  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) proporciona los métodos de la entidad de seguridad que un contenedor se comunica con un control.  administra la activación y la desactivación de controles en contexto.  
  
-   Inicialización de[IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) Combines en una única llamada para ayudar a los contenedores para evitar los retrasos a controles de carga.  
  
-   [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) proporciona interacción mínima del mouse para un control de otro modo inactivo.  
  
## Programa de ejemplo  
 [ATLFire](../top/visual-cpp-samples.md)  
  
## artículos relacionados  
 [tutorial de ATL](../atl/active-template-library-atl-tutorial.md)  
  
## Vea también  
 [Class Overview](../atl/atl-class-overview.md)