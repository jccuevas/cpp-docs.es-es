---
title: "C&#243;digo de vista de registros creado por el Asistente para aplicaciones (acceso a datos MFC) | Microsoft Docs"
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
  - "asistentes para aplicaciones [C++], código de vistas de registros"
  - "vistas de registros, código de asistente para aplicaciones"
  - "vistas de registros, actualizar los controles"
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;digo de vista de registros creado por el Asistente para aplicaciones (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El [Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md) reemplaza las funciones miembro `OnInitialUpdate` y `OnGetRecordset` de la vista.  Después de que el marco cree la ventana de marco, el documento y la vista, llamará a `OnInitialUpdate` para inicializar la vista.  `OnInitialUpdate` obtiene un puntero al conjunto de registros desde el documento.  Una llamada a la función [CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) de clase base abre el conjunto de registros.  El código siguiente muestra este proceso para una `CRecordView`. El código de una `CDaoRecordView` es similar:  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
   m_pSet = &GetDocument()->m_sectionSet;  
   CRecordView::OnInitialUpdate();  
}  
```  
  
 Cuando se abre el conjunto de registros, selecciona los registros.  [CRecordset::Open](../Topic/CRecordset::Open.md) o [CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md) establece el primer registro como registro actual, y DDX mueve los datos de los miembros de datos de campo del conjunto de registros a los correspondientes controles de formulario en la vista.  Para obtener más información sobre RFX, consulte [Intercambio de campos de registros \(RFX\)](../data/odbc/record-field-exchange-rfx.md).  Para obtener más información sobre DDX, consulte [Intercambio y validación de datos del cuadro de diálogo](../mfc/dialog-data-exchange-and-validation.md).  Para obtener información sobre el proceso de creación de documento\/vista, consulte [Utilizar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
> [!NOTE]
>  Debe ofrecer a los usuarios finales la capacidad de actualizar los controles de vista de registros desde el conjunto de registros.  Sin esta capacidad, si un usuario cambia el valor de un control a un valor no válido, puede quedarse bloqueado en el registro actual.  Para actualizar los controles, llame a la función miembro `CWnd` [UpdateData](../Topic/CWnd::UpdateData.md) con un parámetro **FALSE**.  
  
## Vea también  
 [Utilizar una vista de registros](../data/using-a-record-view-mfc-data-access.md)