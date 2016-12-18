---
title: "Clases de plantillas de documentos | Microsoft Docs"
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
  - "vc.classes.document"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas de documento, clases"
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de plantillas de documentos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los objetos de plantilla de documento coordinan la creación de documentos, de la vista, y los objetos de la ventana de marco cuando se crea un nuevo documento o una vista.  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)  
 La clase base para las plantillas de documento.  No utilizará esta clase directamente; en su lugar, utilice una de las otras clases de plantilla de documento derivadas de esta clase.  
  
 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)  
 Una plantilla para los documentos de la interfaz de múltiples documentos \(MDI\).  Las aplicaciones MDI pueden tener varios documentos abiertos al mismo tiempo.  
  
 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)  
 Una plantilla para los documentos de la interfaz de un único documento \(SDI\).  Las aplicaciones SDI sólo tienen un documento abierto al mismo tiempo.  
  
## Clase relacionada  
 [CCreateContext](../mfc/reference/ccreatecontext-structure.md)  
 Una estructura pasada por una plantilla de documento a la ventana\- creación funciona para coordinar la creación de documentos, de la vista, y los objetos de la cuadro\- ventana.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)