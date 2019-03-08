---
title: Clases de compatibilidad de interfaz de usuario (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.ui
helpviewer_keywords:
- user interfaces, support classes
- user interfaces, ATL classes
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
ms.openlocfilehash: 09b7aa26fc2f4597f741865ec94222bd65b85665
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297048"
---
# <a name="ui-support-classes"></a>Clases de compatibilidad de interfaz de usuario

Las clases siguientes proporcionan compatibilidad general de la interfaz de usuario:

- [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) una interfaz para el análisis de HTML de Microsoft y el motor de representación.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) proporciona los métodos de entidad de seguridad a través del cual se comunica un contenedor con un control. Administra la activación y desactivación de los controles en contexto.

- [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md) administra la reactivación de controles en contexto. Habilita un control sin ventana para recibir mensajes, así como para participar en operaciones de arrastrar y colocar.

- [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md) ayuda a la comunicación entre un control in situ y su contenedor.

- [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md) permite a un control para que se muestre directamente y para notificar al contenedor de los cambios en su presentación. Proporciona compatibilidad para el dibujo de parpadeo, controles transparentes y no rectangulares y la prueba de posicionamiento.

## <a name="related-articles"></a>Artículos relacionados

[Tutorial de ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Vea también

[Información general de clases](../atl/atl-class-overview.md)
