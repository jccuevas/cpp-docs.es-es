---
title: "Clases de vistas derivadas disponibles en MFC | Microsoft Docs"
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
  - "clases [C++], derivadas"
  - "CView (clase), clases derivadas de"
  - "clases derivadas, clases de vista"
  - "clases de vista, derivadas"
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de vistas derivadas disponibles en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra las clases y sus relaciones uno otras de la vista MFC.  Las funciones de la clase de vista dependen de la clase de vista de MFC que deriva de.  
  
### Clases de vista  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CView](../mfc/reference/cview-class.md)|Clase base de todos vistas.|  
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Clase base de `CTreeView`, de `CListView`, de `CEditView`, y de `CRichEditView`.  Estas clases permiten utilizar la arquitectura documento\/vista con controles comunes indicados de Windows.|  
|[CEditView](../mfc/reference/ceditview-class.md)|Una vista sencilla basada en el control del cuadro de edición de Windows.  Permite la protección y la edición de texto y se puede utilizar como base para una aplicación de editor de texto simple.  Vea también `CRichEditView`.|  
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Una vista que contiene un objeto de [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) .  Esta clase es análoga a `CEditView`pero, a diferencia de `CEditView`, texto con formato de los identificadores de `CRichEditView` .|  
|[CListView](../mfc/reference/clistview-class.md)|Una vista que contiene un objeto de [CListCtrl](../mfc/reference/clistctrl-class.md) .|  
|[CTreeView](../mfc/reference/ctreeview-class.md)|Una vista que contiene un objeto de [CTreeCtrl](../mfc/reference/ctreectrl-class.md) , para las vistas que se parecen a la ventana del Explorador de soluciones en Visual C\+\+.|  
|[CScrollView](../mfc/reference/cscrollview-class.md)|Clase base de `CFormView`, de `CRecordView`, y de `CDaoRecordView`.  Implementa desplazar el contenido de la vista.|  
|[CFormView](../mfc/reference/cformview-class.md)|Una vista de formulario, una vista que contiene controles.  Una aplicación formulario\- basada proporciona uno o más tales interfaces del formulario.|  
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Una vista de explorador web que el usuario de la aplicación puede examinar sitios en World Wide Web, así como carpetas en el sistema de archivos local y en una red.  La vista explorador web también puede funcionar como un contenedor de documentos activos.|  
|[CRecordView](../mfc/reference/crecordview-class.md)|Una vista de formulario que muestra los registros de base de datos ODBC en controles.  Si selecciona la compatibilidad de ODBC en el proyecto, la clase base de la vista es `CRecordView`.  La vista está conectada a un objeto de `CRowset` .|  
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Una vista de formulario que muestra los registros de base de datos de DAO en controles.  Si selecciona la compatibilidad de DAO en el proyecto, la clase base de la vista es `CDaoRecordView`.  La vista está conectada a un objeto de `CDaoRecordset` .|  
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Una vista de formulario que muestra los registros de OLE DB en controles.  Si selecciona la compatibilidad OLE DB en el proyecto, la clase base de la vista es `COleDBRecordView`.  La vista está conectada a un objeto de `CRowset` .|  
  
> [!NOTE]
>  A partir de la versión 4.0 de MFC, `CEditView` se deriva de `CCtrlView`.  
  
 Para utilizar estas clases en la aplicación, derive las clases de vista de la aplicación de ellas.  Para obtener información relacionada, vea [Vistas de desplazamiento y escala](../mfc/scrolling-and-scaling-views.md).  Para obtener más información sobre las clases de base de datos, vea [Información general: Programación de la base de datos](../data/data-access-programming-mfc-atl.md).  
  
## Vea también  
 [Usar vistas](../mfc/using-views.md)