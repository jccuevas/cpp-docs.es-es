---
title: Ejemplo de puntos de conexión ATL
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: 9312db740171672e6b0f231855408e0d0a9e060d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495997"
---
# <a name="atl-connection-point-example"></a>Ejemplo de puntos de conexión ATL

En este ejemplo se muestra un objeto que admite [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) como una interfaz de salida:

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

Al especificar `IPropertyNotifySink` como una interfaz de salida, puede usar la clase [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) en lugar de `IConnectionPointImpl`. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>Vea también

[Punto de conexión](../atl/atl-connection-points.md)

