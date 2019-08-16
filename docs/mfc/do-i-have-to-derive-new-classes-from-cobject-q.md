---
title: ¿Tengo que derivar las clases nuevas de CObject?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: 30eb3ce5bbb72ab685ed891644a478a36026ebea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352390"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>¿Tengo que derivar las clases nuevas de CObject?

No, no es necesario.

Derive una clase de [CObject](../mfc/reference/cobject-class.md) cuando necesite las funciones ofrece, como la serialización o CObject dinámico. Muchas clases de datos deban serializarse a archivos, por lo que a menudo es una buena idea de derivarlos de `CObject`. Para un ejemplo de una clase derivada de `CObject`, consulte el [ejemplo Scribble](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[CObject (clase): Preguntas más frecuentes](../mfc/cobject-class-frequently-asked-questions.md)
