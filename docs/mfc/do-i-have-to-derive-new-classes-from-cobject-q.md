---
title: ¿Tengo que derivar las clases nuevas de CObject?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: c2361967dcfce5e46aeec65ade3d7056b362949d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636610"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>¿Tengo que derivar las clases nuevas de CObject?

No, no es necesario.

Derive una clase de [CObject](../mfc/reference/cobject-class.md) cuando necesite las funciones ofrece, como la serialización o CObject dinámico. Muchas clases de datos deban serializarse a archivos, por lo que a menudo es una buena idea de derivarlos de `CObject`. Para un ejemplo de una clase derivada de `CObject`, consulte el [ejemplo Scribble](../visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[CObject (clase): Preguntas más frecuentes](../mfc/cobject-class-frequently-asked-questions.md)
