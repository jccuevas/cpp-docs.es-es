---
title: Registre el código de la vista creado por el Asistente para aplicaciones (acceso a datos MFC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 32d969ae0c54e529c53ff35f7d6c84421e848d6c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339108"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Código de vista de registros creado por el Asistente para aplicaciones (acceso a datos MFC)
El [MFC Application Wizard](../mfc/reference/database-support-mfc-application-wizard.md) invalida la vista `OnInitialUpdate` y `OnGetRecordset` funciones miembro. Después de que el marco cree la ventana de marco, el documento y la vista, llamará a `OnInitialUpdate` para inicializar la vista. `OnInitialUpdate` obtiene un puntero al conjunto de registros desde el documento. Una llamada a la clase base [CView:: OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) función abre el conjunto de registros. El código siguiente muestra este proceso para un `CRecordView`:  
  
```cpp  
void CSectionForm::OnInitialUpdate()  
{  
   m_pSet = &GetDocument()->m_sectionSet;  
   CRecordView::OnInitialUpdate();  
}  
```  
  
 Cuando se abre el conjunto de registros, selecciona los registros. [CRecordset:: Open](../mfc/reference/crecordset-class.md#open) hace que el primer registro el registro actual y DDX mueve los datos de los miembros de datos de campo del conjunto de registros a los correspondientes controles de formulario en la vista. Para obtener más información sobre RFX, consulte [intercambio de campos de registros (RFX)](../data/odbc/record-field-exchange-rfx.md). Para obtener más información sobre DDX, consulte [intercambio de datos de cuadro de diálogo y validación](../mfc/dialog-data-exchange-and-validation.md). Para obtener información sobre el proceso de creación de documento/vista, consulte [utilizando las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
> [!NOTE]
>  Debe ofrecer a los usuarios finales la capacidad de actualizar los controles de vista de registros desde el conjunto de registros. Sin esta capacidad, si un usuario cambia el valor de un control a un valor no válido, puede quedarse bloqueado en el registro actual. Para actualizar los controles, llamar a la `CWnd` función miembro [UpdateData](../mfc/reference/cwnd-class.md#updatedata) con un parámetro es False.  
  
## <a name="see-also"></a>Vea también  
 [Uso de una vista de registros](../data/using-a-record-view-mfc-data-access.md)