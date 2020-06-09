---
title: Creación de objetos dinámicos
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 00e627e6d73e510ca694966291e2ef518fef18b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619551"
---
# <a name="dynamic-object-creation"></a>Creación de objetos dinámicos

En este artículo se explica cómo crear un objeto dinámicamente en tiempo de ejecución. El procedimiento usa la información de clase en tiempo de ejecución, como se describe en el artículo [acceso a la información de clase en tiempo de ejecución](accessing-run-time-class-information.md).

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>Crear dinámicamente un objeto a partir de su clase en tiempo de ejecución

1. Use el código siguiente para crear dinámicamente un objeto mediante la `CreateObject` función de `CRuntimeClass` . En caso de error, `CreateObject` devuelve **null** en lugar de generar una excepción:

   [!code-cpp[NVC_MFCCObjectSample#6](codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Consulte también

[Destruir objetos Window](tn017-destroying-window-objects.md) 
 [Usar CObject](using-cobject.md)
