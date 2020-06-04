---
title: Creación de objetos dinámicos
ms.date: 03/27/2020
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
ms.openlocfilehash: 40a17d3ed458d0634fd5bf27b54d0a36a65e35b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364807"
---
# <a name="dynamic-object-creation"></a>Creación de objetos dinámicos

En este artículo se explica cómo crear un objeto dinámicamente en tiempo de ejecución. El procedimiento utiliza información de clase en tiempo de ejecución, como se describe en el artículo Acceso a la información de clase en [tiempo de ejecución](../mfc/accessing-run-time-class-information.md).

#### <a name="dynamically-create-an-object-given-its-run-time-class"></a>Crear dinámicamente un objeto dada su clase en tiempo de ejecución

1. Utilice el código siguiente para crear dinámicamente un objeto mediante la `CreateObject` función del `CRuntimeClass`archivo . En caso `CreateObject` de error, devuelve **NULL** en lugar de generar una excepción:

   [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]

## <a name="see-also"></a>Consulte también

[Destruir objetos](tn017-destroying-window-objects.md)
de ventana[mediante CObject](using-cobject.md)
