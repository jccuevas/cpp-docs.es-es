---
title: "Vistas de registros (acceso a datos MFC) | Microsoft Docs"
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
  - "DAO [C++], vistas de registros"
  - "bases de datos [C++], vistas de registros"
  - "formularios [C++], tareas de acceso a datos"
  - "MFC [C++], vistas de registros"
  - "conjuntos de registros ODBC [C++], vistas de registros"
  - "vistas de registros [C++]"
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vistas de registros (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta sección solo se aplica a las clases ODBC y DAO de MFC.  Para obtener información acerca de las vistas de registros de OLE DB, consulte [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) y [Utilizar las vistas de registros de OLE DB](../data/oledb/using-ole-db-record-views.md).  
  
 Para admitir aplicaciones de acceso a datos basado en formularios, la biblioteca de clases proporciona la clase [CRecordView](../mfc/reference/crecordview-class.md) y la clase [CDaoRecordView](../mfc/reference/cdaorecordview-class.md).  Una vista de registros es un objeto de vista de formulario cuyos controles se asignan directamente a los miembros de datos de campo de un objeto [Recordset](../data/odbc/recordset-odbc.md) \(e indirectamente a las columnas correspondientes de una tabla o resultado de consulta en el origen de datos\).  Al igual que su clase base [CFormView](../mfc/reference/cformview-class.md), `CRecordView` y `CDaoRecordView` se basan en un recurso de plantilla de diálogo.  
  
## Usos de los formularios  
 Los formularios son útiles para varias tareas de acceso a datos:  
  
-   Introducción de datos  
  
-   Realización de análisis de solo lectura de los datos  
  
-   Actualización de datos  
  
## Información adicional sobre vistas de registros  
 El material de los temas se aplica a las clases basadas en ODBC y a las clases basadas en DAO.  Use `CRecordView` para ODBC y `CDaoRecordView` para DAO.  
  
 Entre los temas se incluyen los siguientes:  
  
-   [Características de las clases de vistas de registros](../data/features-of-record-view-classes-mfc-data-access.md)  
  
-   [Intercambio de datos para vistas de registros](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
-   [Rol del programador al utilizar una vista de registros](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
-   [Diseñar y crear una vista de registros](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
-   [Utilizar una vista de registros](../data/using-a-record-view-mfc-data-access.md)  
  
## Vea también  
 [Programación del acceso a datos \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)   
 [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)