---
title: Clases de compatibilidad de interfaz de usuario (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.ui
dev_langs:
- C++
helpviewer_keywords:
- user interfaces, support classes
- user interfaces, ATL classes
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd98d71fe52f9ecfb1410593506ab6487540d4e5
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961960"
---
# <a name="ui-support-classes"></a>Clases de compatibilidad de interfaz de usuario
Las clases siguientes proporcionan compatibilidad general de la interfaz de usuario:  
  
-   [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) una interfaz para el análisis de HTML de Microsoft y el motor de representación.  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) proporciona los métodos de entidad de seguridad a través del cual se comunica un contenedor con un control. Administra la activación y desactivación de los controles en contexto.  
  
-   [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md) administra la reactivación de controles en contexto. Habilita un control sin ventana para recibir mensajes, así como para participar en operaciones de arrastrar y colocar.  
  
-   [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md) ayuda a la comunicación entre un control in situ y su contenedor.  
  
-   [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md) permite a un control para que se muestre directamente y para notificar al contenedor de los cambios en su presentación. Proporciona compatibilidad para el dibujo de parpadeo, controles transparentes y no rectangulares y la prueba de posicionamiento.  
  
## <a name="related-articles"></a>Artículos relacionados  
 [Tutorial de ATL](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../atl/atl-class-overview.md)

