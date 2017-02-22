---
title: "COleDBRecordView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDBRecordView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDBRecordView (clase)"
  - "MFC, OLE DB"
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# COleDBRecordView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una vista que muestra los registros de una base de datos en controles.  
  
## Sintaxis  
  
```  
class COleDBRecordView : public CFormView  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDBRecordView::COleDBRecordView](../Topic/COleDBRecordView::COleDBRecordView.md)|Crea un objeto `COleDBRecordView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDBRecordView::OnGetRowset](../Topic/COleDBRecordView::OnGetRowset.md)|devuelve un valor estándar de `HRESULT` .|  
|[COleDBRecordView::OnMove](../Topic/COleDBRecordView::OnMove.md)|Actualiza el registro actual \(si se ha modificado\) en el origen de datos y después se desplaza al registro especificado \(después, anterior, primero, o último\).|  
  
## Comentarios  
 La vista es una vista de formulario directamente conectada a un objeto de `CRowset` .  La vista se crea de un recurso de plantilla de cuadro de diálogo y muestra los campos del objeto de `CRowset` en los controles de la plantilla de cuadro de diálogo.  El objeto de `COleDBRecordView` utiliza el diálogo intercambio de datos, y la funcionalidad de navegación incorporada en `CRowset`, para automatizar el movimiento de datos entre los controles del formulario y los campos de conjunto de filas.  de`COleDBRecordView` también proporciona una implementación predeterminada para desplazarse al primer registro, siguiente, anterior, o pasado y una interfaz para actualizar el registro actualmente en la vista.  
  
 Se pueden utilizar funciones DDX con **COleDbRecordView** para obtener datos directamente del conjunto de registros de la base de datos y mostrarlos en un control de cuadro de diálogo.  Se deben usar los métodos de **DDX\_\*** \(como `DDX_Text`\), no las funciones **DDX\_Field\*** \(como `DDX_FieldText`\) con **COleDbRecordView**.  `DDX_FieldText` no funcionará con **COleDbRecordView** porque `DDX_FieldText` toma un argumento adicional de **CRecordset\*** tipo \(para `CRecordView`\) o de **CDaoRecordset\*** \(para `CDaoRecordView`\).  
  
> [!NOTE]
>  Si trabaja con las clases \(DAO\) de Objetos de acceso a datos en lugar de las clases para plantillas de consumidor OLE DB, utilice la clase [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) en su lugar.  Para obtener más información, vea el artículo [información general: programación de la base de datos](../../data/data-access-programming-mfc-atl.md).  
  
 `COleDBRecordView` realiza el seguimiento de la posición del usuario en el conjunto de filas de modo que la vista de registros pueda actualizar la interfaz de usuario.  Cuando el usuario mueve a cualquier extremo de conjunto de filas, la vista de registros deshabilita objetos de la interfaz de usuario \(como elementos de menú o botones de la barra de herramientas \(para desplazarse más en la misma dirección.  
  
 Para obtener más información sobre las clases de conjunto de filas, vea el artículo de [Utilizar las plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `COleDBRecordView`  
  
## Requisitos  
 **encabezado:** afxoledb.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)