---
title: 'Controles ATL: Clases de compatibilidad general'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
ms.openlocfilehash: c3d6f7588e333a27a8bc766d982660aaa4d984c9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818614"
---
# <a name="controls-general-support-classes"></a>Controles: Clases de compatibilidad general

Las clases siguientes proporcionan compatibilidad general para los controles ATL:

- [CComControl](../atl/reference/ccomcontrol-class.md) consta de los miembros de datos y funciones auxiliares que son esenciales para controles ATL.

- [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) proporciona los métodos necesarios para los controles.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) proporciona los métodos de entidad de seguridad a través del cual se comunica un contenedor con un control. Administra la activación y desactivación de los controles en contexto.

- [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) combina la inicialización en una única llamada para ayudar a los contenedores de evitar retrasos al cargar los controles.

- [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) proporciona interacción con el mouse mínima para un control inactivo en caso contrario.

## <a name="sample-program"></a>Programa de ejemplo

[ATLFire](../visual-cpp-samples.md)

## <a name="related-articles"></a>Artículos relacionados

[Tutorial de ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Vea también

[Información general de clases](../atl/atl-class-overview.md)
