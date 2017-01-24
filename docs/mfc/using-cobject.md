---
title: "Usar CObject | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject (clase)"
  - "clases derivadas, desde CObject"
  - "ejemplos [MFC], CObject"
  - "MFC, clase base"
  - "clase base del elemento raíz para MFC"
ms.assetid: d0cd19bb-2856-4b41-abbc-620fd64cb223
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar CObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CObject](../mfc/reference/cobject-class.md) es la clase base de la raíz para la mayoría de la biblioteca Microsoft Foundation Class \(MFC\).  La clase de `CObject` contiene muchas funciones útiles que puede que desee incorporar en dispone de objetos del programa, incluida la compatibilidad con la serialización, la información de la clase en tiempo de ejecución, y salida de diagnóstico del objeto.  Si deriva la clase de `CObject`, la clase puede aprovechar estas características de `CObject` .  
  
## ¿Qué desea hacer?  
  
-   [Derive una clase de CObject](../mfc/deriving-a-class-from-cobject.md)  
  
-   [Agregar compatibilidad con la información de la clase en tiempo de ejecución, la creación dinámica, y la serialización a mi clase derivada](../mfc/specifying-levels-of-functionality.md)  
  
-   [Obtener acceso a información de la clase en tiempo de ejecución](../mfc/accessing-run-time-class-information.md)  
  
-   [Cree los objetos dinámicamente](../mfc/dynamic-object-creation.md)  
  
-   [Vuelque los datos de objeto para fines de diagnóstico](http://msdn.microsoft.com/es-es/727855b1-5a83-44bd-9fe3-f1d535584b59)  
  
-   Validar el estado interno del objeto \(vea [MFC ASSERT\_VALID y CObject::AssertValid](http://msdn.microsoft.com/es-es/7654fb75-9e9a-499a-8165-0a96faf2d5e6)\)  
  
-   [Haga que la clase se serialice el almacenamiento persistente](../mfc/serialization-in-mfc.md)  
  
-   Vea una lista de [Preguntas más frecuentes de CObject](../mfc/cobject-class-frequently-asked-questions.md)  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [CRuntimeClass Structure](../mfc/reference/cruntimeclass-structure.md)   
 [Archivos](../mfc/files-in-mfc.md)   
 [Serialización](../mfc/serialization-in-mfc.md)