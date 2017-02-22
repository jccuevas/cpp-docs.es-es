---
title: "Un retrato de la arquitectura documento/vista | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "arquitectura documento/vista"
  - "arquitectura documento/vista, acerca de la arquitectura documento/vista"
  - "arquitectura documento/vista, obtener acceso a datos desde vista"
  - "documentos, obtener acceso a datos desde vista"
  - "documentos, varias vistas"
  - "documentos, vistas"
  - "entrada, clase de vista"
  - "varias vistas, actualizar desde documentos"
  - "vistas, obtener acceso a datos del documento desde"
  - "vistas, y datos proporcionados por el usuario"
  - "vistas, actualizar"
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Un retrato de la arquitectura documento/vista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Documentos y vistas se creen en una aplicación MFC normal.  Los datos se almacena en el documento, pero la vista tiene acceso privilegiado a los datos.  La separación de documento de vista separa el almacenamiento y el mantenimiento de datos de la pantalla.  
  
## Acceso a los datos de la vista  
 La vista tiene acceso a los datos del documento cualquiera con la función de [GetDocument](../Topic/CView::GetDocument.md) , que devuelve un puntero al documento, o creando el c\+\+. `friend` de la clase de vista de la clase del documento.  La vista utilice su acceso a los datos para obtener los datos cuando está listo para dibujarlo o manipular de otra manera.  
  
 Por ejemplo, la función miembro de [OnDraw](../Topic/CView::OnDraw.md) de la vista, la vista utiliza **GetDocument** para obtener un puntero de documento.  Utilice ese puntero para tener acceso a un miembro de datos de `CString` en el documento.  La vista pasa la cadena a la función de `TextOut` .  Para ver el código de este ejemplo, vea [Dibujar en una vista](../mfc/drawing-in-a-view.md).  
  
## Datos proporcionados por el usuario a la vista  
 La vista también podría interpretar un clic del mouse dentro de sí mismo como la selección o edición de datos.  Puede ser que interprete de forma similar pulsaciones de tecla como entrada o la edición.  Supongamos el usuario escribe una cadena en una vista que administra el texto.  La vista obtiene un puntero al documento y usa el puntero para pasar los nuevos datos al documento, que se almacena en un búfer de estructura de datos.  
  
## Actualizar varias vistas del documento del mismo  
 En una aplicación con varias vistas del mismo documento \(como una ventana divisora en un editor de texto \)la vista primero pasa los nuevos datos al documento.  Llama a la función miembro de [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) de documento, que indica a todas las vistas del documento que se actualicen, ajuste los nuevos datos.  Esto sincroniza las vistas.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Ventajas de la arquitectura documento\/vista](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Alternativas a la arquitectura documento\/vista](../mfc/alternatives-to-the-document-view-architecture.md)  
  
## Vea también  
 [Arquitectura documento\/vista](../mfc/document-view-architecture.md)