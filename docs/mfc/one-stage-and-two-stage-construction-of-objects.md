---
title: Construcción de objetos en una fase y en dos fases
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 8f221ac6b63a06c65f932a695dfbf7b93ae7ac96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375969"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Construcción de objetos en una fase y en dos fases

Puede elegir entre dos técnicas para crear objetos gráficos, como plumillas y pinceles:

- *Construcción de una etapa:* construya e inicialice el objeto en una etapa, todo con el constructor.

- *Construcción en dos etapas:* Construya e inicialice el objeto en dos etapas separadas. El constructor crea el objeto y una función de inicialización lo inicializa.

La construcción en dos etapas siempre es más segura. En la construcción de una etapa, el constructor podría producir una excepción si proporciona argumentos incorrectos o se produce un error en la asignación de memoria. Ese problema se evita mediante la construcción de dos etapas, aunque hay que comprobar si hay fallos. En cualquier caso, destruir el objeto es el mismo proceso.

> [!NOTE]
> Estas técnicas se aplican a la creación de cualquier objeto, no solo de objetos gráficos.

## <a name="example-of-both-construction-techniques"></a>Ejemplo de ambas técnicas de construcción

En el ejemplo breve siguiente se muestran ambos métodos para construir un objeto de lápiz:

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Objetos gráficos](../mfc/graphic-objects.md)

- [Selección de un objeto gráfico en un contexto de dispositivo](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Contextos de dispositivos](../mfc/device-contexts.md)

- [Dibujo en una vista](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Consulte también

[Objetos gráficos](../mfc/graphic-objects.md)
