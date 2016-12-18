---
title: "Clases de vistas (Windows) | Microsoft Docs"
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
  - "vc.classes.view"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vistas de formulario y registro"
  - "clases de ventana divisora"
  - "clases de vista, Windows"
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de vistas (Windows)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CView` y sus clases derivadas son ventanas secundarias que representan el área cliente de una ventana de marco.  Las vistas muestran datos y aceptan la entrada de un documento.  
  
 Una clase de vista se asocia a una clase de documento y una clase de ventana de marco utilizando un objeto de plantilla de documento.  
  
 [CView](../mfc/reference/cview-class.md)  
 La clase base para las vistas específicas de la aplicación de los datos de un documento.  Las vistas muestran datos y aceptan datos proporcionados por el usuario para editar o para seleccionar los datos.  Derive la clase o clases de vista de `CView`.  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 La clase base para las vistas con capacidades de desplazamiento.  Derive la clase de vista de `CScrollView` para el desplazamiento automático.  
  
## Formulario y registre las vistas  
 Las vistas de formulario también están adoptando vistas.  Se basan en una plantilla de cuadro de diálogo.  
  
 Las vistas de registros se derivan de las vistas de formulario.  Además de la plantilla en el cuadro de diálogo, también tienen una conexión a una base de datos.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Una vista de desplazamiento cuyo diseño se define en una plantilla de cuadro de diálogo.  Derive una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Proporciona una vista de formulario directamente conectada a un objeto de conjunto de registros de \(DAO\) del Objeto de acceso a datos.  Como todas las vistas de formulario, `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Proporciona una vista de formulario directamente conectada a un objeto de conjunto de registros de ODBC.  Como todas las vistas de formulario, `CRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CHtmlEditView](../mfc/reference/chtmleditview-class.md)  
 Una vista de formulario que proporciona la funcionalidad de la plataforma de edición HTML WebBrowser.  
  
## Vistas de Control  
 Las vistas de Control muestran un control como su vista.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 La clase base para todas las vistas asociado a los controles de Windows.  Las vistas basadas en los controles son descritas debajo.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Una vista que contenga un control de edición estándar de Windows \(vea [CEdit](../mfc/reference/cedit-class.md)\).  Los controles de edición admiten la modificación de texto, busque, reemplazando, y mover funciones.  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 Una vista que contenga un control rich edit de Windows \(vea [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\).  Además de las funciones de un control de edición, los controles rich edit admiten fuentes, colores, formato de párrafo, y objetos OLE incrustados.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Una vista que contenga un control de lista de Windows \(vea [CListCtrl](../mfc/reference/clistctrl-class.md)\).  Un control de lista muestra una colección de elementos, cada uno que consta de un icono y una etiqueta, de manera similar al panel derecho del Explorador de archivos.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Una vista que contiene un control de árbol de Windows \(vea [CTreeCtrl](../mfc/reference/ctreectrl-class.md)\).  Un control de árbol muestra una lista jerárquica de iconos y de una manera similar organizada etiquetas al panel izquierdo del Explorador de archivos.  
  
## Clases relacionadas  
 `CSplitterWnd` permite tener varias vistas dentro de una sola ventana de marco.  `CPrintDialog` y `CPrintInfo` admiten la función de impresión y vista previa de impresión de vistas.  `CRichEditDoc` y `CRichEditCntrItem` se utilizan con `CRichEditView` para implementar funciones VIEJAS del contenedor.  
  
 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)  
 Una ventana que el usuario puede dividir en varios paneles.  Estos paneles pueden ser el usuario puede o de tamaño fijo.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Proporciona un cuadro de diálogo estándar para imprimir un archivo.  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 Una estructura que contiene información sobre un trabajo de impresión o de la vista previa de impresión.  Utilizado por `CView` que imprime la arquitectura.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Mantiene la lista de elementos de OLE de cliente que están en `CRichEditView`.  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 Proporciona acceso de cliente a un elemento OLE almacenado en `CRichEditView`.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)