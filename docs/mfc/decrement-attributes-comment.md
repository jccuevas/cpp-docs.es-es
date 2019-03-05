---
title: --Attributes (comentario)
ms.date: 11/04/2016
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
ms.openlocfilehash: a74d0f9d6ffb0bd2d057cf46f7308d8b6a81f98c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303240"
---
# <a name="-attributes-comment"></a>// Attributes (Comentario)

El `// Attributes` sección de una declaración de clase MFC contiene los atributos (o propiedades) públicos del objeto. Normalmente, son variables de miembro o funciones Get/Set. Las funciones "Get" y "Set" pueden o no pueden ser virtuales. Las funciones de "Get" suelen **const**, porque en la mayoría de los casos no tienen efectos secundarios. Estos miembros son normalmente públicos. atributos privados y protegidos normalmente se encuentran en la sección de implementación.

En el ejemplo de lista de clase `CStdioFile`, en [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md), la lista incluye una variable de miembro, *m_pStream*. Clase `CDC` enumera casi 20 miembros bajo este comentario.

> [!NOTE]
>  Clases grande, como `CDC` y `CWnd`, puede tener tantos miembros que sólo se muestran todos los atributos de un grupo no agregaría confusa. En tales casos, la biblioteca de clases usa otros comentarios como encabezados para delimitar aún más los miembros. Por ejemplo, `CDC` usa `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`y mucho más. Los grupos que representan atributos siguen la sintaxis habitual que se ha descrito anteriormente. Muchas clases OLE tienen una sección de implementación denominada `// Interface Maps`.

## <a name="see-also"></a>Vea también

[Uso de los archivos de código fuente de MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)<br/>
[Implementation (comentario)](../mfc/decrement-implementation-comment.md)<br/>
[Comentario de constructores](../mfc/decrement-constructors-comment.md)<br/>
[Comentario Operations](../mfc/decrement-operations-comment.md)<br/>
[Overridables (comentario)](../mfc/decrement-overridables-comment.md)
