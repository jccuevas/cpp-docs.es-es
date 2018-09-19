---
title: Uso de vistas de registros de OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ba772afc5cd4c1dd1cf6014339c8779bec476b48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058580"
---
# <a name="using-ole-db-record-views"></a>Utilizar las vistas de registros de OLE DB

Si desea mostrar los datos del conjunto de filas de OLE DB en una aplicación MFC, debe usar la clase MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Crea un objeto de vista de registros desde `COleDBRecordView` permite mostrar registros de base de datos en controles MFC. La vista de registros es una vista de formulario de cuadro de diálogo conectada directamente a un objeto Rowset de OLE DB creado a partir de la `CRowset` clase de plantilla. Obtener un identificador para el objeto de conjunto de filas es sencillo:  
  
```cpp  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
La vista muestra los campos de la `CRowset` objeto en los controles del cuadro de diálogo. El `COleDBRecordView` objeto utiliza el intercambio de datos de cuadro de diálogo (DDX) y la funcionalidad de exploración integrada en `CRowset` (`MoveFirst`, `MoveNext`, `MovePrev`, y `MoveLast`) para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de filas. `COleDBRecordView` realiza un seguimiento de la posición del usuario en el conjunto de filas para que la vista de registros pueda actualizar la interfaz de usuario y proporciona un [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) método para actualizar el registro actual antes de pasar a otro.  
  
Puede utilizar funciones DDX con `COleDbRecordView` para obtener datos directamente desde el conjunto de registros de base de datos y mostrarlos en un control de cuadro de diálogo. Debe usar el **DDX_** <strong>\*</strong> métodos (como `DDX_Text`), no el **DDX_Field** <strong>\*</strong> funciones (como `DDX_FieldText`) con `COleDbRecordView`.  
  
## <a name="see-also"></a>Vea también  

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)<br/>
[COleDBRecordView (clase)](../../mfc/reference/coledbrecordview-class.md)