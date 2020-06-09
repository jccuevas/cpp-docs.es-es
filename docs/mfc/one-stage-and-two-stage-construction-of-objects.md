---
title: Construcción de objetos en una fase y en dos fases
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 07e006d5b326486c54f23990c604a7d2ee0e4c83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625285"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Construcción de objetos en una fase y en dos fases

Puede elegir entre dos técnicas para crear objetos gráficos, como lápices y pinceles:

- *Construcción en una fase*: construya e inicialice el objeto en una fase, todo ello con el constructor.

- *Construcción en dos fases*: construya e inicialice el objeto en dos fases independientes. El constructor crea el objeto y una función de inicialización lo inicializa.

La construcción en dos fases siempre es más segura. En la construcción de una fase, el constructor podría producir una excepción si se proporcionan argumentos incorrectos o se produce un error en la asignación de memoria. Este problema se evita mediante la construcción en dos fases, aunque es necesario comprobar si hay errores. En cualquier caso, la destrucción del objeto es el mismo proceso.

> [!NOTE]
> Estas técnicas se aplican a la creación de objetos, no solo a objetos gráficos.

## <a name="example-of-both-construction-techniques"></a>Ejemplo de ambas técnicas de construcción

En el siguiente ejemplo breve se muestran ambos métodos para construir un objeto Pen:

[!code-cpp[NVC_MFCDocViewSDI#6](codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Objetos gráficos](graphic-objects.md)

- [Seleccionar un objeto gráfico en un contexto de dispositivo](selecting-a-graphic-object-into-a-device-context.md)

- [Contextos de dispositivo](device-contexts.md)

- [Dibujo en una vista](drawing-in-a-view.md)

## <a name="see-also"></a>Consulte también

[Objetos gráficos](graphic-objects.md)
