---
title: Usar los archivos de código fuente de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: 6f23f792f750e4352494bf3e4bde08f0fe360439
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980490"
---
# <a name="using-the-mfc-source-files"></a>Usar los archivos de código fuente de MFC

La biblioteca de Microsoft Foundation Class (MFC) proporciona código fuente completo. Los archivos de encabezado (. h) se encuentran en el directorio \atlmfc\include. los archivos de implementación (. cpp) se encuentran en el directorio \atlmfc\src\mfc

En esta familia de artículos se explican las convenciones que MFC usa para comentar las distintas partes de cada clase, lo que significan estos comentarios y lo que se espera encontrar en cada sección. Los asistentes C++ visuales usan convenciones similares para las clases que crean automáticamente, y es probable que encuentre estas convenciones útiles para su propio código.

Es posible que esté familiarizado con las palabras clave **Public**, **Protected**y **Private** C++ . En los archivos de encabezado de MFC, encontrará que cada clase puede tener varias de cada una de ellas. Por ejemplo, las funciones y variables de miembro público pueden estar en más de una palabra clave **Public** . Se debe a que MFC separa las variables y funciones de miembro según su uso, no por el tipo de acceso permitido. MFC utiliza de forma moderada. Incluso los elementos considerados detalles de implementación suelen estar **protegidos**y muchas veces son **públicas**. Aunque no se recomienda el acceso a los detalles de implementación, MFC deja de tomar la decisión.

En los archivos de código fuente de MFC y en los archivos de encabezado creados por el Asistente para aplicaciones MFC, encontrará comentarios como los que se incluyen en las declaraciones de clase (normalmente en este orden):

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

Los temas que se tratan en esta familia de artículos incluyen:

- [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)

- [Comentario de implementación//](../mfc/decrement-implementation-comment.md)

- [Comentario//constructores](../mfc/decrement-constructors-comment.md)

- [El comentario//Attributes](../mfc/decrement-attributes-comment.md)

- [El comentario//Operations](../mfc/decrement-operations-comment.md)

- [Comentario//reemplazables](../mfc/decrement-overridables-comment.md)

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
