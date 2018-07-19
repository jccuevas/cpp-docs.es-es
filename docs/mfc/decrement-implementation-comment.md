---
title: --Implementation (comentario) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89f87c33abfec7b9d055b589726639fcd741e59d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930279"
---
# <a name="-implementation-comment"></a>// Implementation (Comentario)
El `// Implementation` sección es la parte más importante de cualquier declaración de clase MFC.  
  
 Esta sección contiene todos los detalles de implementación. Las variables miembro y funciones miembro pueden aparecer en esta sección. Todos los elementos por debajo de esta línea pudieron cambiar en futuras versiones de MFC. A menos que se no se puede evitar, no debe confiar en los detalles a continuación la `// Implementation` línea. Además, los miembros declarados debajo de la línea de implementación no están documentados, aunque parte de la implementación se describe en notas técnicas. Reemplazos de funciones virtuales en la clase base se encuentran en esta sección, independientemente de qué sección de la función de clase base está definida, porque el hecho de que una función reemplaza la implementación de la clase base se considera un detalle de implementación. Normalmente, estos miembros están protegidos, pero no siempre.  
  
 Tenga en cuenta desde el `CStdioFile` enumerar en [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md) que los miembros declarados bajo el `// Implementation` comentario puede declararse como **pública**, **protegido**, o **privada**. Sólo se deben utilizar a estos miembros con precaución, ya que pueden variar en el futuro. Declarar un grupo de miembros como **público** puede ser necesaria para la implementación de la biblioteca de clase para que funcione correctamente. Sin embargo, esto no significa que puede utilizar los miembros declarados por lo que de forma segura.  
  
> [!NOTE]
>  Puede encontrar los comentarios de los tipos restantes encima o debajo de la `// Implementation` comentario. En cualquier caso, describen los tipos de miembros declarados debajo de ellos. Si se encuentran por debajo del `// Implementation` comentario, debe suponer que los miembros pueden cambiar en versiones futuras de MFC.  
  
## <a name="see-also"></a>Vea también  
 [Usar los archivos de código fuente MFC](../mfc/using-the-mfc-source-files.md)   
 [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)   
 [Comentario de constructores](../mfc/decrement-constructors-comment.md)   
 [Comentario Attributes](../mfc/decrement-attributes-comment.md)   
 [Comentario Operations](../mfc/decrement-operations-comment.md)   
 [Comentarios reemplazables](../mfc/decrement-overridables-comment.md)

