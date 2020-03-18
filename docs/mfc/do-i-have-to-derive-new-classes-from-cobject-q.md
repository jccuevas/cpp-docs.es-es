---
title: ¿Tengo que derivar las clases nuevas de CObject?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: d38e589f371fc56f5566c56de7b19c366065a503
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446923"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>¿Tengo que derivar las clases nuevas de CObject?

No, no.

Derive una clase de [CObject](../mfc/reference/cobject-class.md) cuando necesite las funciones que proporciona, como la serialización o la posibilidad de que se pueda crear la funcionalidad dinámica. Muchas clases de datos se deben serializar en archivos, por lo que a menudo es una buena idea derivarlas de `CObject`. Para obtener un ejemplo de una clase derivada de `CObject`, vea el [ejemplo Scribble](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Consulte también

[CObject (clase): Preguntas más frecuentes](../mfc/cobject-class-frequently-asked-questions.md)
