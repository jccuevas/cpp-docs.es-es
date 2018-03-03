---
title: --Comentarios reemplazables | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Overridables comment in MFC source files
- MFC source files, Overridables comment
- overriding, Overridables comment in MFC source files
- comments, MFC
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca52bcc3846971af1811551411199785c3d4e102
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="-overridables-comment"></a>// Overridables (Comentario)
La `// Overridables` sección de una declaración de clase MFC contiene funciones virtuales que se pueden reemplazar en una clase derivada cuando necesite modificar el comportamiento de la clase base. Suelen denominarse comenzando con "On", aunque no es estrictamente necesaria. Funciones aquí están diseñadas para reemplazarse y a menudo implementan o proporcionan a algún tipo de "devolución de llamada" o "enlazar". Normalmente, estos miembros están protegidos.  
  
 En MFC, las funciones virtuales puras siempre se colocan en esta sección. Una función virtual pura en C++ es uno de la forma:  
  
 `virtual void OnDraw( ) = 0;`  
  
 En el ejemplo de lista de clase `CStdioFile`, en [un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md), la lista no incluye ninguna sección se pueden sobrecargar. Clase **CDocument**, por otro lado, enumera aproximadamente 10 funciones miembro reemplazables.  
  
 En algunas clases, también puede ver el comentario `// Advanced Overridables`. Estas son funciones superiores a solo los programadores deben intentar reemplazar. Probablemente nunca necesitará invalidarlas.  
  
> [!NOTE]
>  Las convenciones descritas en este artículo también funcionan bien, en general, para las propiedades y métodos de automatización (antes conocida como automatización OLE). Métodos de automatización son similares a las operaciones de MFC. Propiedades de automatización son similares a los atributos MFC. Eventos de automatización (admitidos para controles ActiveX, anteriormente conocidos como controles OLE) son similares a las funciones miembro reemplazables de MFC.  
  
## <a name="see-also"></a>Vea también  
 [Usar los archivos de código fuente MFC](../mfc/using-the-mfc-source-files.md)   
 [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)   
 [Implementation (comentario)](../mfc/decrement-implementation-comment.md)   
 [Comentario de constructores](../mfc/decrement-constructors-comment.md)   
 [Comentario Attributes](../mfc/decrement-attributes-comment.md)   
 [Comentario Operations](../mfc/decrement-operations-comment.md)

