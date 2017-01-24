---
title: "Utilizar las vistas de registros de OLE DB | Microsoft Docs"
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
  - "COleDBRecordView (clase), información general"
  - "MFC, vistas de registros"
  - "vistas de registros OLE DB"
  - "OLE DB, vistas de registros"
  - "vistas de registros, objetos de vistas de registros"
  - "conjuntos de filas, vistas de registros"
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar las vistas de registros de OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si desea mostrar datos de un conjunto de filas OLE DB en una aplicación MFC, debe usar la clase MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md).  Un objeto de vista de registros creado a partir de `COleDBRecordView` permite mostrar registros de base de datos en controles MFC.  La vista de registro es una vista de formulario de cuadro de diálogo conectada directamente a un objeto Rowset OLE DB creado a partir de la clase de plantilla `CRowset`.  Obtener un identificador del objeto de conjunto de filas es sencillo:  
  
```  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 La vista muestra los campos del objeto `CRowset` en los controles del cuadro de diálogo.  El objeto `COleDBRecordView` utiliza Intercambio de datos de cuadro de diálogo \(DDX\) y la funcionalidad de navegación incorporada en `CRowset` \(**MoveFirst**, `MoveNext`, `MovePrev` y `MoveLast`\) para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de filas.  `COleDBRecordView` realiza el seguimiento de la posición del usuario en el conjunto de filas, de forma que la vista del registro puede actualizar la interfaz de usuario, y proporciona un método [OnMove](../Topic/COleDBRecordView::OnMove.md) para actualizar el registro actual antes de desplazarse a otro.  
  
 Se pueden utilizar funciones DDX con **COleDbRecordView** para obtener datos directamente del conjunto de registros de la base de datos y mostrarlos en un control de cuadro de diálogo.  Se deben usar los métodos de **DDX\_\*** \(como `DDX_Text`\), no las funciones **DDX\_Field\*** \(como `DDX_FieldText`\) con **COleDbRecordView**.  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)   
 [COleDBRecordView Class](../../mfc/reference/coledbrecordview-class.md)