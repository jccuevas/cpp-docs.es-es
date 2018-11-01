---
title: ¿Qué costo tiene derivar una clase de CObject?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: 521b6a32e3e5b34b4da9dab3117d55a728bd8e88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500456"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>¿Qué costo tiene derivar una clase de CObject?

La sobrecarga de derivar de la clase [CObject](../mfc/reference/cobject-class.md) es mínimo. La clase derivada hereda solo cuatro funciones virtuales y una sola [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objeto.

## <a name="see-also"></a>Vea también

[CObject (clase): Preguntas más frecuentes](../mfc/cobject-class-frequently-asked-questions.md)
