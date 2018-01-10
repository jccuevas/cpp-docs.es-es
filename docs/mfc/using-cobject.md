---
title: Usar CObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CObject
dev_langs: C++
helpviewer_keywords:
- examples [MFC], CObject
- root base class for MFC
- derived classes [MFC], from CObject
- MFC, base class
- CObject class [MFC]
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17bffb412975cfc6a97eae8b30aff2514a2e1d93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-cobject"></a>Usar CObject
[CObject](../mfc/reference/cobject-class.md) es la clase base raíz para la mayor parte de la biblioteca de clases de Microsoft Foundation (MFC). La `CObject` clase contiene muchas características útiles que se pueden incorporar en sus propios objetos de programa, incluida la compatibilidad con la serialización, información de clase en tiempo de ejecución y salida de diagnóstico del objeto. Si se deriva la clase de `CObject`, la clase puede aprovechar estas `CObject` características.  
  
## <a name="what-do-you-want-to-do"></a>Qué quieres hacer  
  
-   [Derivar una clase de CObject](../mfc/deriving-a-class-from-cobject.md)  
  
-   [Agregar compatibilidad para obtener información de clase en tiempo de ejecución, la creación dinámica y la serialización a la clase derivada](../mfc/specifying-levels-of-functionality.md)  
  
-   [Información de clase en tiempo de ejecución de acceso](../mfc/accessing-run-time-class-information.md)  
  
-   [Crear objetos de forma dinámica](../mfc/dynamic-object-creation.md)  
  
-   [Volcar los datos del objeto con fines de diagnóstico](http://msdn.microsoft.com/en-us/727855b1-5a83-44bd-9fe3-f1d535584b59)  
  
-   Validar el estado del objeto interno (consulte [MFC ASSERT_VALID y CObject:: AssertValid](http://msdn.microsoft.com/en-us/7654fb75-9e9a-499a-8165-0a96faf2d5e6))  
  
-   [Tiene la clase serializar a sí mismo al almacenamiento persistente](../mfc/serialization-in-mfc.md)  
  
-   Ver una lista de [preguntas más frecuentes acerca de CObject](../mfc/cobject-class-frequently-asked-questions.md)  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [Estructura de CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)   
 [Archivos](../mfc/files-in-mfc.md)   
 [Serialización](../mfc/serialization-in-mfc.md)

