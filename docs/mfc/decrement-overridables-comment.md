---
title: --Overridables (comentario) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Overridables comment in MFC source files
- MFC source files, Overridables comment
- overriding, Overridables comment in MFC source files
- comments, MFC
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d50fb62767f2130e89cb75df5d66f8c18ce2a097
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428062"
---
# <a name="-overridables-comment"></a>// Overridables (Comentario)

El `// Overridables` sección de una declaración de clase MFC contiene funciones virtuales que se pueden reemplazar en una clase derivada cuando necesite modificar el comportamiento de la clase base. Normalmente se denominan empezando por "On", aunque no es estrictamente necesario. Las funciones aquí están diseñadas para invalidarse y a menudo implementar o proporcionar a algún tipo de "devolución de llamada" o "enlazar". Normalmente, estos miembros están protegidos.

En MFC, las funciones virtuales puras siempre se colocan en esta sección. Una función virtual pura en C++ es uno de la forma:

`virtual void OnDraw( ) = 0;`

En el ejemplo de lista de clase `CStdioFile`, en [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md), la lista no incluye ninguna sección reemplazables. Clase `CDocument`, por otro lado, enumera aproximadamente 10 funciones miembro reemplazables.

En algunas clases, también puede ver el comentario `// Advanced Overridables`. Estas son funciones que sólo avanzados a los programadores deben intentar reemplazar. Probablemente nunca tendrá que reemplazarlos.

> [!NOTE]
>  Las convenciones descritas en este artículo también funcionan bien, en general, para propiedades y métodos de automatización (antes conocida como automatización OLE). Métodos de automatización son similares a las operaciones de MFC. Propiedades de automatización son similares a los atributos MFC. Eventos de automatización (admitidos para los controles ActiveX, conocidos anteriormente como controles OLE) son similares a las funciones miembro reemplazables de MFC.

## <a name="see-also"></a>Vea también

[Uso de los archivos de código fuente de MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)<br/>
[Implementation (comentario)](../mfc/decrement-implementation-comment.md)<br/>
[Comentario de constructores](../mfc/decrement-constructors-comment.md)<br/>
[Comentario Attributes](../mfc/decrement-attributes-comment.md)<br/>
[Comentario Operations](../mfc/decrement-operations-comment.md)

