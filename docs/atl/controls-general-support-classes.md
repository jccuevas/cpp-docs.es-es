---
title: 'Controles ATL: Clases de compatibilidad general'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
ms.openlocfilehash: 3f00348ab0c9f25bdd4f6b7a2b05cd4b82ea48e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262819"
---
# <a name="controls-general-support-classes"></a>Controles: Clases de compatibilidad general

Las clases siguientes proporcionan compatibilidad general para los controles ATL:

- [CComControl](../atl/reference/ccomcontrol-class.md) consta de los miembros de datos y funciones auxiliares que son esenciales para controles ATL.

- [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) proporciona los métodos necesarios para los controles.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) proporciona los métodos de entidad de seguridad a través del cual se comunica un contenedor con un control. Administra la activación y desactivación de los controles en contexto.

- [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) combina la inicialización en una única llamada para ayudar a los contenedores de evitar retrasos al cargar los controles.

- [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) proporciona interacción con el mouse mínima para un control inactivo en caso contrario.

## <a name="sample-program"></a>Programa de ejemplo

[ATLFire](../overview/visual-cpp-samples.md)

## <a name="related-articles"></a>Artículos relacionados

[Tutorial de ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Vea también

[Información general de clases](../atl/atl-class-overview.md)
