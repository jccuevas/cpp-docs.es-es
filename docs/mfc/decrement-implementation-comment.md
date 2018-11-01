---
title: --Implementation (comentario)
ms.date: 11/04/2016
helpviewer_keywords:
- Implementation comment in MFC source files
- comments, MFC
- MFC source files, Implementation comment
- comments, Implementation comments
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
ms.openlocfilehash: ab69fa25cc8dece635097f17bae97f831f7ec87f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552898"
---
# <a name="-implementation-comment"></a>// Implementation (Comentario)

El `// Implementation` sección es la parte más importante de cualquier declaración de clase MFC.

Esta sección contiene todos los detalles de implementación. Variables de miembro y funciones miembro pueden aparecer en esta sección. Todo bajo esta línea podría cambiar en futuras versiones de MFC. A menos que no se puede evitar, no debe confiar en los detalles a continuación el `// Implementation` línea. Además, los miembros declarados debajo de la línea de implementación no están documentados, aunque parte de la implementación se describe en las notas técnicas. Reemplazos de funciones virtuales en la clase base se encuentran en esta sección, independientemente de qué sección de la función de la clase base está definida, ya que el hecho de que una función invalida la implementación de la clase base se considera un detalle de implementación. Normalmente, estos miembros están protegidos, pero no siempre.

Tenga en cuenta desde la `CStdioFile` listado en [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md) que los miembros declarados bajo el `// Implementation` comentario puede declararse como **pública**, **protegido**, o **privada**. Solo se deben usar a estos miembros con precaución, ya que pueden variar en el futuro. Declarar un grupo de miembros como **pública** puede ser necesario para la implementación de la biblioteca de clase para que funcione correctamente. Sin embargo, esto no significa que los miembros declarados por lo que puede utilizar sin ningún riesgo.

> [!NOTE]
>  Puede encontrar los comentarios de los tipos restantes encima o debajo de la `// Implementation` comentario. En cualquier caso, describen los tipos de miembros declarados debajo de ellos. Si aparecen a continuación el `// Implementation` comentario, debe suponer que los miembros pueden cambiar en futuras versiones de MFC.

## <a name="see-also"></a>Vea también

[Uso de los archivos de código fuente de MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)<br/>
[Comentario de constructores](../mfc/decrement-constructors-comment.md)<br/>
[Comentario Attributes](../mfc/decrement-attributes-comment.md)<br/>
[Comentario Operations](../mfc/decrement-operations-comment.md)<br/>
[Overridables (comentario)](../mfc/decrement-overridables-comment.md)

