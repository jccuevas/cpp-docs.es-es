---
title: "CRecordView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRecordView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecordView (clase)"
  - "conjuntos de registros ODBC, viewing records"
  - "registros, viewing ODBC"
  - "vistas, ODBC"
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CRecordView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una vista que muestra los registros de una base de datos en controles.  
  
## Sintaxis  
  
```  
class AFX_NOVTABLE CRecordView : public CFormView  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordView::CRecordView](../Topic/CRecordView::CRecordView.md)|Crea un objeto `CRecordView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordView::IsOnFirstRecord](../Topic/CRecordView::IsOnFirstRecord.md)|Devuelve cero si el registro actual es el primer registro del conjunto de registros asociado.|  
|[CRecordView::IsOnLastRecord](../Topic/CRecordView::IsOnLastRecord.md)|Devuelve cero si el registro actual es el último registro en el conjunto de registros asociado.|  
|[CRecordView::OnGetRecordset](../Topic/CRecordView::OnGetRecordset.md)|devuelve un puntero a un objeto de una clase derivada de `CRecordset`.  ClassWizard reemplaza esta función para usted y crea el conjunto de registros en caso necesario.|  
|[CRecordView::OnMove](../Topic/CRecordView::OnMove.md)||  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecordView::OnMove](../Topic/CRecordView::OnMove.md)|Si el registro actual ha cambiado, se actualiza en el origen de datos, después desplaza el registro especificado \(después, anterior, primero, o último\).|  
  
## Comentarios  
 La vista es una vista de formulario directamente conectada a un objeto de `CRecordset` .  La vista se crea de un recurso de plantilla de cuadro de diálogo y muestra los campos del objeto de `CRecordset` en los controles de la plantilla de cuadro de diálogo.  El objeto de `CRecordView` utiliza el intercambio de intercambio de datos y de registro del diálogo de campo \(RFX\) para automatizar el movimiento de datos entre los controles del formulario y los campos de conjunto de registros.  de`CRecordView` también proporciona una implementación predeterminada para desplazarse al primer registro, siguiente, anterior, o pasado y una interfaz para actualizar el registro actualmente en la vista.  
  
> [!NOTE]
>  Si trabaja con las clases \(DAO\) de Objetos de acceso a datos en lugar de las clases de ODBC, utilice la clase [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) en su lugar.  Para obtener más información, vea el artículo [información general: programación de la base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 La manera más común de crear la vista de registros es con el Asistente para aplicaciones.  El Asistente para aplicaciones de Tge crea tanto la clase de vista de registros y la clase asociado de conjunto de registros como parte de la aplicación esqueleto inicial.  Si no crea la clase de vista de registros con el Asistente para aplicaciones, puede que sea más adelante con ClassWizard.  Si necesita simplemente un único formulario, el enfoque del Asistente para aplicaciones es más fácil.  ClassWizard permite decidir utilizar una vista de registros más adelante en el proceso de desarrollo.  Mediante ClassWizard crear una vista de registros y un conjunto de registros por separado y después conectarlos es el enfoque más flexible porque proporciona más control en llamar a la clase de conjunto de registros y su. archivos de H\/.CPP.  Este enfoque también permite obtener vistas de registros se crean en la misma clase de conjunto de registros.  
  
 Para facilitar a los usuarios finales se trasladen de registros de la vista de registros, el Asistente para aplicaciones crear los recursos de menú \(y opcionalmente barra de herramientas\) para el registro que se mueve a la primera, siguiente, anterior, o último.  Si crea una clase de vista de registros con ClassWizard, necesita crear estos recursos personalmente con el menú y editores bitmap.  
  
 Para obtener información sobre la implementación predeterminada para desplazarse de un registro a otro, vea `IsOnFirstRecord` y `IsOnLastRecord` y el caso [Utilizar una vista de registros](../../data/using-a-record-view-mfc-data-access.md).  
  
 `CRecordView` realiza el seguimiento de la posición del usuario en el conjunto de registros para que la vista de registros pueda actualizar la interfaz de usuario.  Cuando el usuario mueve a cualquier extremo de conjunto de registros, la vista de registros deshabilita objetos de la interfaz de usuario \(como elementos de menú o botones de la barra de herramientas \(para desplazarse más en la misma dirección.  
  
 Para obtener más información sobre cómo declarar y utilizar las clases de vista de registros y de conjunto de registros, vea “Diseñar y crear una vista de registros” en el artículo [Grabe las vistas](../../data/record-views-mfc-data-access.md).  Para obtener más información sobre cómo funcionan las vistas de registros y cómo utilizarlos, vea el artículo [Utilizar una vista de registros](../../data/using-a-record-view-mfc-data-access.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CRecordView`  
  
## Requisitos  
 **encabezado:** afxdb.h  
  
## Vea también  
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)