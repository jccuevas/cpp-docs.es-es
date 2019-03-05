---
title: Construcción de objetos en una fase y en dos fases
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 871db7abd2682d557bf2e80e9cb97624f0dc53a6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263642"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Construcción de objetos en una fase y en dos fases

Tiene la posibilidad de elegir entre dos técnicas para crear objetos gráficos, como lápices y pinceles:

- *Construcción de una fase*: Construir e inicializar el objeto en una fase, todo ello con el constructor.

- *Construcción en dos fases*: Construir e inicializar el objeto en dos fases independientes. El constructor crea el objeto y lo inicializa una función de inicialización.

Construcción en dos fases siempre es más seguro. En la construcción de una fase, el constructor podría producir una excepción si se proporcionan argumentos incorrectos o se produce un error de asignación de memoria. Se evita este problema mediante la construcción de dos fases, aunque tiene comprobación de errores. En cualquier caso, destruir el objeto es el mismo proceso.

> [!NOTE]
>  Estas técnicas se aplican a la creación de cualquier objeto, no sólo de objetos gráficos.

## <a name="example-of-both-construction-techniques"></a>Ejemplo de ambas técnicas de construcción

En el siguiente ejemplo se muestra ambos métodos de creación de un objeto pen:

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Objetos gráficos](../mfc/graphic-objects.md)

- [Seleccionar un objeto gráfico en un contexto de dispositivo](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Contextos de dispositivo](../mfc/device-contexts.md)

- [Dibujo en una vista](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Vea también

[Objetos gráficos](../mfc/graphic-objects.md)
