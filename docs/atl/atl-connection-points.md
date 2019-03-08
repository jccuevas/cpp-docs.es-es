---
title: Puntos de conexión en ATL
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: 4d94396ef8839516d9bfee15a2611cce66baa6bd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297832"
---
# <a name="atl-connection-points"></a>Puntos de conexión en ATL

Un objeto conectable es aquel que acepta interfaces de salida. Una interfaz de salida permite que el objeto se comunique con un cliente. Para cada interfaz de salida, el objeto conectable expone un punto de conexión. Cada interfaz de salida es implementada por un cliente en un objeto denominado receptor.

![Puntos de conexión](../atl/media/vc2zw31.gif "puntos de conexión")

Cada punto de conexión es compatible con la [IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint) interfaz. El objeto conectable expone sus puntos de conexión al cliente a través de la [IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer) interfaz.

## <a name="in-this-section"></a>En esta sección

[Clases de puntos de conexión ATL](../atl/atl-connection-point-classes.md)<br/>
Describe brevemente las clases ATL compatibles con puntos de conexión.

[Agregar puntos de conexión a un objeto](../atl/adding-connection-points-to-an-object.md)<br/>
Describe los pasos utilizados para agregar puntos de conexión a un objeto.

[Ejemplo de puntos de conexión ATL](../atl/atl-connection-point-example.md)<br/>
Proporciona un ejemplo de cómo declarar un punto de conexión.

## <a name="related-sections"></a>Secciones relacionadas

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)
