---
title: Grabar vistas (acceso a datos MFC) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38c5d65e89aa4fb76ff96fa82cd52e42475e2353
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="record-views--mfc-data-access"></a>Vistas de registros (acceso a datos MFC)
Esta sección solo se aplica a las clases ODBC de MFC. Para obtener información acerca de las vistas de registros de OLE DB, vea [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) y [utilizando OLE DB vistas de registros](../data/oledb/using-ole-db-record-views.md).  
  
 Para admitir aplicaciones de acceso a datos basado en formularios, la biblioteca de clases proporciona la clase [CRecordView](../mfc/reference/crecordview-class.md). Una vista de registros es un objeto de vista de formulario cuyos controles se asignan directamente a los miembros de datos de campo de un [recordset](../data/odbc/recordset-odbc.md) objeto (e indirectamente a las columnas correspondientes de un resultado de la consulta o una tabla en el origen de datos). Al igual que su clase base [CFormView](../mfc/reference/cformview-class.md), `CRecordView` se basa en un recurso de plantilla de cuadro de diálogo.  
  
## <a name="form-uses"></a>Usos de los formularios  
 Los formularios son útiles para varias tareas de acceso a datos:  
  
-   Introducción de datos  
  
-   Realización de análisis de solo lectura de los datos  
  
-   Actualización de datos  
  
## <a name="further-reading-about-record-views"></a>Información adicional sobre vistas de registros  
 El material de los temas se aplica a las clases basadas en ODBC y a las clases basadas en DAO. Use `CRecordView` para ODBC y `CDaoRecordView` para DAO.  
  
 Entre los temas se incluyen los siguientes:  
  
-   [Características de clases de vista de registros](../data/features-of-record-view-classes-mfc-data-access.md)  
  
-   [Intercambio de datos para vistas de registros](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
-   [El rol cuando se trabaja con una vista de registros](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
-   [Diseñar y crear una vista de registros](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
-   [Utilizar una vista de registros](../data/using-a-record-view-mfc-data-access.md)  
  
## <a name="see-also"></a>Vea también  
 [Acceso a los datos de programación (MFC/ATL)](../data/data-access-programming-mfc-atl.md)   
 [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)