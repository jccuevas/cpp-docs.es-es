---
title: Mediante vistas de registros de OLE DB | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03e88eaafa82e346c720810bf567d867a9cd6096
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-ole-db-record-views"></a>Utilizar las vistas de registros de OLE DB
Si desea mostrar los datos de conjunto de filas de OLE DB en una aplicación MFC, debe usar la clase MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Crea un objeto de vista de registros desde `COleDBRecordView` permite mostrar registros de base de datos en controles MFC. La vista de registros es una vista de formulario de cuadro de diálogo conectada directamente a un objeto Rowset OLE DB creado a partir de la `CRowset` clase de plantilla. Obtener un identificador para el objeto de conjunto de filas es sencillo:  
  
```  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 La vista muestra los campos de la `CRowset` objeto en los controles de cuadro de diálogo. El `COleDBRecordView` objeto utiliza el intercambio de datos de cuadro de diálogo (DDX) y la funcionalidad de exploración integrada en `CRowset` (**MoveFirst**, `MoveNext`, `MovePrev`, y `MoveLast`) para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de filas. `COleDBRecordView`realiza un seguimiento de la posición del usuario en el conjunto de filas para que la vista de registros pueda actualizar la interfaz de usuario y suministra un [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) método para actualizar el registro actual antes de pasar a otro.  
  
 Puede utilizar funciones DDX con **COleDbRecordView** para obtener datos directamente desde el conjunto de registros de base de datos y mostrarlos en un control de cuadro de diálogo. Debe utilizar el **DDX_\***  métodos (como `DDX_Text`), no el **DDX_Field\***  funciones (como `DDX_FieldText`) con **COleDbRecordView** .  
  
## <a name="see-also"></a>Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)   
 [COleDBRecordView (clase)](../../mfc/reference/coledbrecordview-class.md)