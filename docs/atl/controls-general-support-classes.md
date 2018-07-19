---
title: 'Controles ATL: Compatibilidad con clases General | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.controls
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c0aa30487edb3a5998a0b9777017015aeb7b675
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354860"
---
# <a name="controls-general-support-classes"></a>Controles: Clases de soporte General
Las clases siguientes proporcionan compatibilidad general para los controles ATL:  
  
-   [CComControl](../atl/reference/ccomcontrol-class.md) consta de los miembros de funciones y datos de la aplicación auxiliar son esenciales para controles ATL.  
  
-   [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) proporciona los métodos necesarios para los controles.  
  
-   [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) proporciona los métodos de entidad de seguridad a través del cual se comunica un contenedor con un control. Administra la activación y desactivación de los controles en contexto.  
  
-   [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) combina la inicialización en una sola llamada a evitar contenedores retrasos al cargar los controles.  
  
-   [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) proporciona interacción con el mouse mínimo para un control inactivo en caso contrario.  
  
## <a name="sample-program"></a>Programa de ejemplo  
 [ATLFire](../visual-cpp-samples.md)  
  
## <a name="related-articles"></a>Artículos relacionados  
 [Tutorial ATL](../atl/active-template-library-atl-tutorial.md)  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../atl/atl-class-overview.md)

