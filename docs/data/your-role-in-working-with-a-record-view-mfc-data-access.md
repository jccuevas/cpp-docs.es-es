---
title: "Rol del programador al utilizar una vista de registros (acceso a datos MFC) | Microsoft Docs"
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
  - "MFC, vistas de registros"
  - "vistas de registros, personalizar el código predeterminado"
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rol del programador al utilizar una vista de registros (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La siguiente tabla muestra qué se debe hacer normalmente para trabajar con una vista de registros y qué tareas realiza el marco de trabajo.  
  
### Trabajar con una vista de registros: el programador y el marco de trabajo  
  
|El programador|El marco de trabajo|  
|--------------------|-------------------------|  
|Utiliza el editor de cuadros de diálogo de Visual C\+\+ para diseñar el formulario.|Crea un recurso de plantilla de cuadro de diálogo con controles.|  
|Usa el [Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md) para crear clases derivadas de [CRecordView](../mfc/reference/crecordview-class.md) y [CRecordset](../mfc/reference/crecordset-class.md) o de [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) y [CDaoRecordset](../mfc/reference/cdaorecordset-class.md).|Escribe las clases.|  
|Asigna controles de vista de registros a miembros de datos de campo de conjuntos de registros.|Proporciona DDX entre los controles y los campos de conjuntos de registros.|  
||Proporciona controladores de comandos predeterminados para los comandos **Mover primero**, **Mover último**, **Mover siguiente** y **Mover anterior** de los menús o botones de la barra de herramientas.|  
||Actualiza los cambios en el origen de datos.|  
|\[Opcional\] Escribe código para rellenar cuadros de lista, cuadros combinados u otros controles con datos de otro conjunto de registros.||  
|\[Opcional\] Escribe código para las validaciones especiales.||  
|\[Opcional\] Escribe código para agregar o eliminar registros.||  
  
 La programación basada en formularios es solo una forma de trabajar con una base de datos.  Para obtener información sobre las aplicaciones con otra interfaz de usuario o sin interfaz de usuario, consulte [MFC: Utilizar clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md) y [MFC: Utilizar clases de base de datos sin documentos ni vistas](../data/mfc-using-database-classes-without-documents-and-views.md).  Para conocer otras maneras de mostrar registros de la base de datos, consulte las clases [CListView](../mfc/reference/clistview-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md).  
  
## Vea también  
 [Vistas de registros \(acceso a datos MFC\)](../data/record-views-mfc-data-access.md)   
 [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)