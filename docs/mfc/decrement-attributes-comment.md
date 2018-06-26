---
title: --Atributos comentario | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44b34c2e2d22d0a0a2feb15f6bf2793b68dc7042
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929574"
---
# <a name="-attributes-comment"></a>// Attributes (Comentario)
La `// Attributes` sección de una declaración de clase MFC contiene los atributos (o propiedades) públicos del objeto. Normalmente se trata de variables de miembro o funciones Get/Set. Las funciones "Get" y "Set" pueden o no pueden ser virtuales. Las funciones "Get" suelen **const**, porque en la mayoría de los casos no tienen efectos secundarios. Estos miembros son normalmente públicos; atributos protegidos y privados normalmente se encuentran en la sección de implementación.  
  
 En el ejemplo de lista de clase `CStdioFile`, en [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md), la lista incluye una variable miembro, *m_pStream*. Clase `CDC` casi 20 miembros bajo este comentario se enumeran.  
  
> [!NOTE]
>  Clases de gran tamaño, como `CDC` y `CWnd`, puede tener tantos miembros que una lista de todos los atributos de un grupo no agregaría confusa. En tales casos, la biblioteca de clases usa otros comentarios como encabezados para delimitar aún más los miembros. Por ejemplo, `CDC` utiliza `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`y mucho más. Grupos que representan atributos seguirá la sintaxis habitual que se ha descrito anteriormente. Muchas clases OLE tienen una sección de implementación denominada `// Interface Maps`.  
  
## <a name="see-also"></a>Vea también  
 [Usar los archivos de código fuente MFC](../mfc/using-the-mfc-source-files.md)   
 [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)   
 [Implementation (comentario)](../mfc/decrement-implementation-comment.md)   
 [Comentario de constructores](../mfc/decrement-constructors-comment.md)   
 [Comentario Operations](../mfc/decrement-operations-comment.md)   
 [Comentarios reemplazables](../mfc/decrement-overridables-comment.md)

