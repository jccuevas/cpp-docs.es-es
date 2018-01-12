---
title: Clases de soporte de interfaz de usuario (ATL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.ui
dev_langs: C++
helpviewer_keywords:
- user interfaces, support classes
- user interfaces, ATL classes
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 717e6cfc00c3d2442426698d910baac3c7fcb829
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ui-support-classes"></a>Clases de soporte técnico de la interfaz de usuario
Las clases siguientes proporcionan compatibilidad de interfaz de usuario general:  
  
-   [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) una interfaz para el análisis de HTML de Microsoft y el motor de representación.  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) proporciona los métodos de entidad de seguridad a través del cual se comunica un contenedor con un control. Administra la activación y desactivación de los controles en contexto.  
  
-   [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md) administra la reactivación de controles in situ. Permite que un control sin ventana para recibir mensajes, así como participar en operaciones de arrastrar y colocar.  
  
-   [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md) ayuda a la comunicación entre un control in situ y su contenedor.  
  
-   [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md) permite que un control para mostrar sí directamente y para notificar al contenedor de los cambios en su presentación. Proporciona compatibilidad para dibujar parpadeo, controles transparentes y no rectangulares y la prueba de posicionamiento.  
  
## <a name="related-articles"></a>Artículos relacionados  
 [Tutorial ATL](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../atl/atl-class-overview.md)

