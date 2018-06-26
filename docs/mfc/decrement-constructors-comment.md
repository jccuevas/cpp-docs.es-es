---
title: ': Comentario de constructores | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f58c8410de51a4692dd0e7f018d40eaa28c0dae8
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929587"
---
# <a name="-constructors-comment"></a>// Constructors (Comentario)
La `// Constructors` sección de una declaración de clase MFC declara constructores (en el sentido de C++), así como las funciones de inicialización requeridas para utilizar realmente el objeto. Por ejemplo, `CWnd::Create` está en la sección de constructores porque antes de usar el `CWnd` objeto, debe ser "construirse por completo" primero llamando al constructor de C++ y, a continuación, llame a la `Create` (función). Normalmente, estos miembros son públicos.  
  
 Por ejemplo, la clase `CStdioFile` tiene tres constructores, uno de los cuales se muestra en la lista bajo [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar los archivos de código fuente MFC](../mfc/using-the-mfc-source-files.md)   
 [Implementation (comentario)](../mfc/decrement-implementation-comment.md)   
 [Comentario Attributes](../mfc/decrement-attributes-comment.md)   
 [Comentario Operations](../mfc/decrement-operations-comment.md)   
 [Comentarios reemplazables](../mfc/decrement-overridables-comment.md)

