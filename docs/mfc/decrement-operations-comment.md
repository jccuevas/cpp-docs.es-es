---
title: --Comentario operations | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 63b3d7a313f0f725444ba77612d8b53280393640
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="-operations-comment"></a>// Operations (Comentario)
La `// Operations` sección de una declaración de clase MFC contiene funciones de miembro que se pueden llamar en el objeto para que sea lo ni realizar acciones (realizar operaciones). Estas funciones son normalmente no -**const** porque normalmente tienen efectos secundarios. Pueden ser virtuales o no virtuales según las necesidades de la clase. Normalmente, estos miembros son públicos.  
  
 En el ejemplo de lista de clase `CStdioFile`, en [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md), la lista incluye dos funciones miembro bajo este comentario: `ReadString` y `WriteString`.  
  
 Al igual que con los atributos, las operaciones se pueden subdividir.  
  
## <a name="see-also"></a>Vea también  
 [Usar los archivos de código fuente MFC](../mfc/using-the-mfc-source-files.md)   
 [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)   
 [Implementation (comentario)](../mfc/decrement-implementation-comment.md)   
 [Comentario de constructores](../mfc/decrement-constructors-comment.md)   
 [Comentario Attributes](../mfc/decrement-attributes-comment.md)   
 [Comentarios reemplazables](../mfc/decrement-overridables-comment.md)

