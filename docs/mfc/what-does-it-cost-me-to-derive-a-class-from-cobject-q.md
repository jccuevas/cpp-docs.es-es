---
title: ¿Qué costo tiene derivar una clase de CObject?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- CObject class [MFC], overhead of derived classes [MFC]
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
ms.openlocfilehash: de760a2fd2908595314dc09cf5a317da3581e3bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186054"
---
# <a name="what-does-it-cost-me-to-derive-a-class-from-cobject"></a>¿Qué costo tiene derivar una clase de CObject?

La sobrecarga de derivar de la clase [CObject](../mfc/reference/cobject-class.md) es mínimo. La clase derivada hereda solo cuatro funciones virtuales y una sola [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objeto.

## <a name="see-also"></a>Vea también

[CObject (clase): Preguntas más frecuentes](../mfc/cobject-class-frequently-asked-questions.md)
