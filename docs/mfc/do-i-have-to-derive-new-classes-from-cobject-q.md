---
title: ¿Tengo que derivar las clases nuevas de CObject?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: 371ede0f0921182c066b4cb224e66b18eb6f1208
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616740"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>¿Tengo que derivar las clases nuevas de CObject?

No, no.

Derive una clase de [CObject](reference/cobject-class.md) cuando necesite las funciones que proporciona, como la serialización o la posibilidad de que se pueda crear la funcionalidad dinámica. Muchas clases de datos se deben serializar en archivos, por lo que a menudo es una buena idea derivarlas de `CObject` . Para obtener un ejemplo de una clase derivada de `CObject` , vea el [ejemplo Scribble](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Consulte también

[CObject (clase): Preguntas más frecuentes](cobject-class-frequently-asked-questions.md)
