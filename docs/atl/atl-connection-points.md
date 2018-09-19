---
title: Puntos de conexión ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe2cf03debbfd88f19ccc77d3922a9a5c50a50d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091275"
---
# <a name="atl-connection-points"></a>Puntos de conexión en ATL

Un objeto conectable es aquel que acepta interfaces de salida. Una interfaz de salida permite que el objeto se comunique con un cliente. Para cada interfaz de salida, el objeto conectable expone un punto de conexión. Cada interfaz de salida es implementada por un cliente en un objeto denominado receptor.

![Puntos de conexión](../atl/media/vc2zw31.gif "vc2zw31")

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

