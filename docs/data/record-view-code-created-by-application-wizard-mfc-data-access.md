---
title: Código de vista de registros creado por el Asistente para aplicaciones (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69bebe978d03e5777f20765ac0bcf9a344f69320
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209162"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Código de vista de registros creado por el Asistente para aplicaciones (acceso a datos MFC)

El [Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md) invalida las funciones miembro `OnInitialUpdate` y `OnGetRecordset` de la vista. Después de que el marco cree la ventana de marco, el documento y la vista, llamará a `OnInitialUpdate` para inicializar la vista. `OnInitialUpdate` obtiene un puntero al conjunto de registros desde el documento. Una llamada a la función [CView:: OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) de la clase base abre el conjunto de registros. En el código siguiente se muestra este proceso para un `CRecordView`:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Cuando se abre el conjunto de registros, selecciona los registros. [CRecordset:: Open](../mfc/reference/crecordset-class.md#open) hace que el primer registro sea el registro actual y DDX mueve los datos de los miembros de datos de campo del conjunto de registros a los controles de formulario correspondientes en la vista. Para obtener más información sobre RFX, consulte [intercambio de campos de registros (RFX)](../data/odbc/record-field-exchange-rfx.md). Para obtener más información sobre DDX, consulte [Intercambio y validación de datos de cuadro de diálogo](../mfc/dialog-data-exchange-and-validation.md). Para obtener información sobre el proceso de creación de documentos y vistas, vea [usar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
>  Debe ofrecer a los usuarios finales la capacidad de actualizar los controles de vista de registros desde el conjunto de registros. Sin esta capacidad, si un usuario cambia el valor de un control a un valor no válido, puede quedarse bloqueado en el registro actual. Para actualizar los controles, llame a la función miembro `CWnd` [UpdateData](../mfc/reference/cwnd-class.md#updatedata) con un parámetro false.

## <a name="see-also"></a>Consulte también

[Usar una vista de registros](../data/using-a-record-view-mfc-data-access.md)
