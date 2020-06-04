---
title: Código de vista de registros creado por el Asistente para aplicaciones (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69481299980329b98e378f02e090670fa3d7ece2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376020"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Código de vista de registros creado por el Asistente para aplicaciones (acceso a datos MFC)

El [Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md) `OnInitialUpdate` reemplaza `OnGetRecordset` las funciones de vista y miembro. Después de que el marco cree la ventana de marco, el documento y la vista, llamará a `OnInitialUpdate` para inicializar la vista. `OnInitialUpdate` obtiene un puntero al conjunto de registros desde el documento. Una llamada a la clase base [CView::OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) función abre el conjunto de registros. El código siguiente muestra `CRecordView`este proceso para:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Cuando se abre el conjunto de registros, selecciona los registros. [CRecordset::Open](../mfc/reference/crecordset-class.md#open) hace que el primer registro sea el registro actual y DDX mueve los datos de los miembros de datos de campo del conjunto de registros a los controles de formulario correspondientes en la vista. Para obtener más información acerca de RFX, vea Intercambio de campos de [registros (RFX)](../data/odbc/record-field-exchange-rfx.md). Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../mfc/dialog-data-exchange-and-validation.md). Para obtener información sobre el proceso de creación de documentos/vistas, consulte Uso de [las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
> Debe ofrecer a los usuarios finales la capacidad de actualizar los controles de vista de registros desde el conjunto de registros. Sin esta capacidad, si un usuario cambia el valor de un control a un valor no válido, puede quedarse bloqueado en el registro actual. Para actualizar los controles, `CWnd` llame a la función miembro [UpdateData](../mfc/reference/cwnd-class.md#updatedata) con un parámetro de FALSE.

## <a name="see-also"></a>Consulte también

[Utilizar una vista de registros](../data/using-a-record-view-mfc-data-access.md)
