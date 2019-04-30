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
ms.openlocfilehash: e0d02af016a0c7bfb0869b7cdd30fe0db2975102
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240866"
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
