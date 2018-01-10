---
title: ': Comentario de constructores | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f6425252df34936d4ba3c9013664205b0038d82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="-constructors-comment"></a>// Constructors (Comentario)
La `// Constructors` sección de una declaración de clase MFC declara constructores (en el sentido de C++), así como las funciones de inicialización requeridas para utilizar realmente el objeto. Por ejemplo, `CWnd::Create` está en la sección de constructores porque antes de usar el `CWnd` objeto, debe ser "construirse por completo" primero llamando al constructor de C++ y, a continuación, llame a la **crear** función. Normalmente, estos miembros son públicos.  
  
 Por ejemplo, la clase `CStdioFile` tiene tres constructores, uno de los cuales se muestra en la lista bajo [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar los archivos de código fuente MFC](../mfc/using-the-mfc-source-files.md)   
 [Implementation (comentario)](../mfc/decrement-implementation-comment.md)   
 [Comentario Attributes](../mfc/decrement-attributes-comment.md)   
 [Comentario Operations](../mfc/decrement-operations-comment.md)   
 [Comentarios reemplazables](../mfc/decrement-overridables-comment.md)

