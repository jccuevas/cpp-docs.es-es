---
title: "Ventajas de la arquitectura documento/vista | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "arquitectura documento/vista, ventajas de"
  - "vistas, ventajas"
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ventajas de la arquitectura documento/vista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La ventaja fundamental de utilizar la arquitectura documento\/vista de MFC es que la arquitectura admite varias vistas del mismo documento particularmente. \(Si no necesita varias vistas y la pequeña sobrecarga de documento y vista es excesiva en la aplicación, puede evitar la arquitectura.  [Alternativas a la arquitectura documento\/vista](../mfc/alternatives-to-the-document-view-architecture.md).\)  
  
 Suponga que la aplicación permite datos numéricos de los usuarios ven en forma de la hoja de cálculo o en forma de gráfico.  Un usuario puede desear ver simultáneamente los datos sin formato, en forma de la hoja de cálculo, y un gráfico que los resultados de los datos.  Se muestra estas vistas independientes en ventanas independientes de marco o en paneles del divisor dentro de una sola ventana.  Suponga ahora que el usuario puede modificar los datos de la hoja de cálculo y ver los cambios reflejan inmediatamente en el gráfico.  
  
 En MFC, la vista hoja de cálculo y la vista de gráfico se basadas en las diferentes clases derivadas de CView.  Ambas vistas se asociadas a un único objeto de documento.  El documento almacena los datos \(o quizás se obtiene de una base de datos\).  Ambas vistas tienen acceso al documento y muestra los datos que recuperan de.  
  
 Cuando un usuario actualiza una de las vistas, ese objeto de vista llama `CDocument::UpdateAllViews`.  Que la función notifica las vistas de todo el documento, y las actualizaciones de cada propia vista utilizando los datos más recientes del documento.  La única llamada a `UpdateAllViews` sincroniza las vistas diferentes.  
  
 Este escenario sería difícil el código sin separación de datos de la vista, especialmente si las vistas almacenados los datos propios.  Con el documento o la vista, es fácil.  Hace el marco de la mayoría del trabajo de coordinación automáticamente.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Alternativas al documento\/vista](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [CDocument](../mfc/reference/cdocument-class.md)  
  
-   [CView](../mfc/reference/cview-class.md)  
  
-   [CDocument::UpdateAllViews](../Topic/CDocument::UpdateAllViews.md)  
  
-   [CView::GetDocument](../Topic/CView::GetDocument.md)  
  
## Vea también  
 [Arquitectura documento\/vista](../mfc/document-view-architecture.md)