---
title: --Constructors (comentario)
ms.date: 11/04/2016
helpviewer_keywords:
- constructors comment
- declarations, constructors
- MFC source files, Constructors comment
- declaring constructors, code comments
- comments, MFC
- comments, constructors comment
- constructors [MFC], declaring
- instance constructors, code comments
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
ms.openlocfilehash: ee36ad991f2a19211b494010d6ff0a5338b80557
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480709"
---
# <a name="-constructors-comment"></a>// Constructors (Comentario)

El `// Constructors` sección de una declaración de clase MFC declara constructores (en el sentido de C++), así como las funciones de inicialización necesarias para utilizar realmente el objeto. Por ejemplo, `CWnd::Create` está en la sección de constructores porque antes de usar el `CWnd` objeto, debe ser "totalmente construido" llamar primero al constructor de C++ y, a continuación, llamando a la `Create` función. Normalmente, estos miembros son públicos.

Por ejemplo, la clase `CStdioFile` tiene tres constructores, uno de los cuales se muestra en la lista de [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md).

## <a name="see-also"></a>Vea también

[Uso de los archivos de código fuente de MFC](../mfc/using-the-mfc-source-files.md)<br/>
[Implementation (comentario)](../mfc/decrement-implementation-comment.md)<br/>
[Comentario Attributes](../mfc/decrement-attributes-comment.md)<br/>
[Comentario Operations](../mfc/decrement-operations-comment.md)<br/>
[Overridables (comentario)](../mfc/decrement-overridables-comment.md)

