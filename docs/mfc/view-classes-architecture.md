---
title: "Clases de vistas (Arquitectura) | Microsoft Docs"
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
  - "vistas de control"
  - "vistas de formulario y registro"
  - "clases de vista"
  - "clases de vista, arquitectura"
ms.assetid: 8894579a-1436-441e-b985-83711061e495
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de vistas (Arquitectura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CView` y sus clases derivadas son ventanas secundarias que representan el área cliente de una ventana de marco.  Las vistas muestran datos y aceptan la entrada de un documento.  
  
 Una clase de vista se asocia a una clase de documento y una clase de ventana de marco utilizando un objeto de plantilla de documento.  
  
 [CView](../mfc/reference/cview-class.md)  
 La clase base para las vistas específicas de la aplicación de los datos de un documento.  Las vistas muestran datos y aceptan datos proporcionados por el usuario para editar o para seleccionar los datos.  Derive la clase de vista de `CView`.  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 La clase base para las vistas con capacidades de desplazamiento.  Derive la clase de vista de `CScrollView` para el desplazamiento automático.  
  
## Formulario y registre las vistas  
 Las vistas de formulario también están adoptando vistas.  Se basan en una plantilla de cuadro de diálogo.  
  
 Las vistas de registros se derivan de las vistas de formulario.  Además de la plantilla en el cuadro de diálogo, también tienen una conexión a una base de datos.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Una vista de desplazamiento cuyo diseño se define en una plantilla de cuadro de diálogo.  Derive una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Proporciona una vista de formulario directamente conectada a un objeto de conjunto de registros de \(DAO\) del Objeto de acceso a datos.  Como todas las vistas de formulario, `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CHtmlView](../mfc/reference/chtmlview-class.md)  
 Admite un control para la exploración del Web dentro de una aplicación.  El control admite HTML dinámico en MFC.  
  
 [COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)  
 Proporciona compatibilidad con MFC OLE DB para las vistas de formulario.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Proporciona una vista de formulario directamente conectada a un objeto de conjunto de registros de ODBC.  Como todas las vistas de formulario, `CRecordView` se basa en una plantilla de cuadro de diálogo.  
  
## Vistas de Control  
 Las vistas de Control muestran un control como su vista.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 La clase base para todas las vistas asociado a los controles de Windows.  Las vistas basadas en los controles son descritas debajo.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Una vista que contenga un control de edición estándar de Windows \(vea [CEdit](../mfc/reference/cedit-class.md)\).  Los controles de edición admiten la modificación de texto, busque, reemplazando, y mover funciones.  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 Una vista que contenga un control rich edit de Windows \(vea [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\).  Además de las funciones de un control de edición, los controles rich edit admiten fuentes, colores, formato de párrafo, y objetos OLE incrustados.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Una vista que contenga un control de lista de Windows \(vea [CListCtrl](../mfc/reference/clistctrl-class.md)\).  Un control de lista muestra iconos y cadenas de manera similar al panel derecho del Explorador de archivos.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Una vista que contiene un control de árbol de Windows \(vea [CTreeCtrl](../mfc/reference/ctreectrl-class.md)\).  Iconos y cadenas de se muestra un control de árbol organizados en una jerarquía de una manera similar al panel izquierdo del Explorador de archivos.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)