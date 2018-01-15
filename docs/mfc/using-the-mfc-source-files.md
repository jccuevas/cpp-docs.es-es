---
title: "Mediante la MFC archivos de código fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 930c205ffd690c190f68766f7a51c83b68ef8d2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-mfc-source-files"></a>Usar los archivos de código fuente de MFC
La biblioteca (Microsoft Foundation Classes) proporciona el código fuente completo. Archivos de encabezado (. h) están en el directorio \atlmfc\include; archivos de implementación (.cpp) están en el directorio \atlmfc\src\mfc.  
  
 Esta serie de artículos explica las convenciones que utiliza MFC para comentar las distintas partes de cada clase, lo que significan estos comentarios y qué se puede esperar encontrar en cada sección. Los asistentes de Visual C++ usan convenciones similares para las clases que crean para usted y probablemente encontrará estas convenciones útil para su propio código.  
  
 Es posible que esté familiarizado con la **público**, `protected`, y `private` palabras clave de C++. Al examinar los archivos de encabezado MFC, encontrará que cada clase puede tener varios de cada uno de ellos. Por ejemplo, podrían ser funciones y variables de miembro público en más de un **público** palabra clave. Esto es porque MFC separa las variables miembro y funciones que se basan en su uso, no por el tipo de acceso permitido. MFC utiliza `private` con moderación; incluso elementos consideran detalles de implementación suelen estar protegidos y muchas veces son públicos. Aunque no se recomienda el acceso a los detalles de implementación, MFC deja la decisión para usted.  
  
 En los archivos de código fuente MFC y los archivos que crea el Asistente para aplicaciones MFC, encontrará comentarios como éstos en las declaraciones de clase (normalmente en este orden):  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 Entre los temas tratados en esta serie de artículos se incluyen:  
  
-   [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)  
  
-   [El / / comentario de implementación](../mfc/decrement-implementation-comment.md)  
  
-   [El / / Constructors (comentario)](../mfc/decrement-constructors-comment.md)  
  
-   [El / / Attributes comentario](../mfc/decrement-attributes-comment.md)  
  
-   [El / / comentario de las operaciones](../mfc/decrement-operations-comment.md)  
  
-   [El / / Overridables comment](../mfc/decrement-overridables-comment.md)  
  
## <a name="see-also"></a>Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)

