---
title: Uso de vistas de registros de OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: febb247e96669951ea24b3e1633fa0857a6acf7c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083209"
---
# <a name="using-ole-db-record-views"></a>Utilizar las vistas de registros de OLE DB

Si desea mostrar los datos del conjunto de filas de OLE DB en una aplicación MFC, utilice la clase MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Crea un objeto de vista de registros desde `COleDBRecordView` permite mostrar registros de base de datos en controles MFC. La vista de registros es una vista de formulario de cuadro de diálogo conectada directamente a un objeto Rowset de OLE DB creado a partir de la `CRowset` clase de plantilla. Obtener un identificador para el objeto de conjunto de filas es simple:

```cpp
COleDBRecordView myRecordView;
...
// CProductAccessor is a user record class
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();
```

La vista muestra los campos de la `CRowset` objeto en los controles del cuadro de diálogo. El `COleDBRecordView` objeto utiliza el intercambio de datos de cuadro de diálogo (DDX) y la funcionalidad de exploración integrada en `CRowset` (`MoveFirst`, `MoveNext`, `MovePrev`, y `MoveLast`) para automatizar el movimiento de datos entre los controles del formulario y los campos del conjunto de filas. `COleDBRecordView` realiza un seguimiento de la posición del usuario en el conjunto de filas para que la vista de registros pueda actualizar la interfaz de usuario y proporciona un [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) método para actualizar el registro actual antes de pasar a otro.

Puede utilizar funciones DDX con `COleDbRecordView` para obtener datos directamente desde el conjunto de registros de base de datos y mostrarlos en un control de cuadro de diálogo. Use la **DDX_** <strong>\*</strong> métodos (como `DDX_Text`), no el **DDX_Field** <strong>\*</strong> funciones () como `DDX_FieldText`) con `COleDbRecordView`.

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)<br/>
[COleDBRecordView (clase)](../../mfc/reference/coledbrecordview-class.md)<br/>
