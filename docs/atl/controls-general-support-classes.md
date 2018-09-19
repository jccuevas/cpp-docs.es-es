---
title: 'Los controles ATL: Clases de compatibilidad General | Microsoft Docs'
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
ms.openlocfilehash: 18bf4bf2d2081402762026d6f26bd4650f9908fe
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751451"
---
# <a name="controls-general-support-classes"></a>Los controles: Clases de compatibilidad General

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

