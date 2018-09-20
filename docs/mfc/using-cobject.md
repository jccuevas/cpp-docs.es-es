---
title: Usar CObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f421624f16a11f02dc260ce95a9d2cf11fcd9fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399137"
---
# <a name="using-cobject"></a>Usar CObject

[CObject](../mfc/reference/cobject-class.md) es la clase base raíz para la mayor parte de la biblioteca de clases de Microsoft Foundation (MFC). La `CObject` clase contiene muchas características útiles que puede incorporar en sus propios objetos de programa, incluida la compatibilidad con la serialización, la información de clase en tiempo de ejecución y salida de diagnóstico del objeto. Si se deriva la clase de `CObject`, la clase puede aprovechar estos `CObject` características.

## <a name="what-do-you-want-to-do"></a>Qué quieres hacer

- [Derivar una clase de CObject](../mfc/deriving-a-class-from-cobject.md)

- [Agregar compatibilidad para la información de clases en tiempo de ejecución, la creación dinámica y la serialización en mi clase derivada](../mfc/specifying-levels-of-functionality.md)

- [Información de la clase de tiempo de ejecución de Access](../mfc/accessing-run-time-class-information.md)

- [Crear objetos de forma dinámica](../mfc/dynamic-object-creation.md)

- [Volcar los datos del objeto para fines de diagnóstico](/previous-versions/visualstudio/visual-studio-2010/sc15kz85\(v=vs.100\))

- Validar el estado interno del objeto (consulte [MFC ASSERT_VALID y CObject:: AssertValid](reference/diagnostic-services.md#assert_valid))

- [Tiene la clase serializarse en un almacenamiento persistente](../mfc/serialization-in-mfc.md)

- Ver una lista de [preguntas más frecuentes acerca de CObject](../mfc/cobject-class-frequently-asked-questions.md)

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CRuntimeClass (estructura)](../mfc/reference/cruntimeclass-structure.md)<br/>
[Archivos](../mfc/files-in-mfc.md)<br/>
[Serialización](../mfc/serialization-in-mfc.md)

