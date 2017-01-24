---
title: "CDaoRecordView Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoRecordView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asistentes para aplicaciones [C++], creating record views"
  - "controles enlazados [C++], displaying database data"
  - "CDaoRecordView (clase)"
  - "controles [MFC], enlace de datos"
  - "enlace de datos [C++], DAO views"
  - "controles enlazados a datos [C++], controles DAO"
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoRecordView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una vista que muestra los registros de una base de datos en controles.  
  
## Sintaxis  
  
```  
  
class AFX_NOVTABLE CDaoRecordView : public CFormView  
  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoRecordView::CDaoRecordView](../Topic/CDaoRecordView::CDaoRecordView.md)|Crea un objeto `CDaoRecordView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoRecordView::IsOnFirstRecord](../Topic/CDaoRecordView::IsOnFirstRecord.md)|Devuelve cero si el registro actual es el primer registro del conjunto de registros asociado.|  
|[CDaoRecordView::IsOnLastRecord](../Topic/CDaoRecordView::IsOnLastRecord.md)|Devuelve cero si el registro actual es el último registro en el conjunto de registros asociado.|  
|[CDaoRecordView::OnGetRecordset](../Topic/CDaoRecordView::OnGetRecordset.md)|devuelve un puntero a un objeto de una clase derivada de `CDaoRecordset`.  ClassWizard reemplaza esta función para usted y crea el conjunto de registros en caso necesario.|  
|[CDaoRecordView::OnMove](../Topic/CDaoRecordView::OnMove.md)|Si el registro actual ha cambiado, se actualiza en el origen de datos, después desplaza el registro especificado \(después, anterior, primero, o último\).|  
  
## Comentarios  
 La vista es una vista de formulario directamente conectada a un objeto de `CDaoRecordset` .  La vista se crea de un recurso de plantilla de cuadro de diálogo y muestra los campos del objeto de `CDaoRecordset` en los controles de la plantilla de cuadro de diálogo.  El diálogo de aplicaciones de objeto de `CDaoRecordView` de intercambio de datos \(DDX\) y intercambio de campos del registro de DAO \(DFX\) para automatizar el movimiento de datos entre los controles del formulario y los campos de conjunto de registros.  `CDaoRecordView` también proporciona una implementación predeterminada para desplazarse al primer registro, siguiente, anterior, o pasado y una interfaz para actualizar el registro actualmente en la vista.  
  
> [!NOTE]
>  Las clases de base de datos de DAO son distintas de las clases de base de datos MFC basadas en ODBC.  Todos los nombres de clase de base de datos de DAO tienen el prefijo “CDao”.  Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO; las clases DAO suelen proporcionar capacidades máximas porque utilizan el motor de base de datos Microsoft Jet.  
  
 La manera más común de crear la vista de registros es con el Asistente para aplicaciones.  El Asistente para aplicaciones crea tanto la clase de vista de registros y la clase asociada de conjunto de registros como parte de su aplicación esqueleto inicial.  
  
 Si necesita simplemente un único formulario, el enfoque del Asistente para aplicaciones es más fácil.  ClassWizard permite decidir utilizar una vista de registros más adelante en el proceso de desarrollo.  Si no crea la clase de vista de registros con el Asistente para aplicaciones, puede que sea más adelante con ClassWizard.  Mediante ClassWizard crear una vista de registros y un conjunto de registros por separado y después conectarlos es el enfoque más flexible porque proporciona más control en llamar a la clase de conjunto de registros y su. archivos de H\/.CPP.  Este enfoque también permite obtener vistas de registros se crean en la misma clase de conjunto de registros.  
  
 Para facilitar a los usuarios finales se trasladen de registros de la vista de registros, el Asistente para aplicaciones crear los recursos de menú \(y opcionalmente barra de herramientas\) para el registro que se mueve a la primera, siguiente, anterior, o último.  Si crea una clase de vista de registros con ClassWizard, necesita crear estos recursos personalmente con el menú y editores bitmap.  
  
 Para obtener información sobre la implementación predeterminada para desplazarse de un registro a otro, vea `IsOnFirstRecord` y `IsOnLastRecord` y el caso [Utilizar una vista de registros](../../data/using-a-record-view-mfc-data-access.md), que se aplica a `CRecordView` y a `CDaoRecordView`.  
  
 `CDaoRecordView` realiza el seguimiento de la posición del usuario en el conjunto de registros para que la vista de registros pueda actualizar la interfaz de usuario.  Cuando el usuario mueve a cualquier extremo de conjunto de registros, la vista de registros deshabilita objetos de la interfaz de usuario \(como elementos de menú o botones de la barra de herramientas \(para desplazarse más en la misma dirección.  
  
 Para obtener más información sobre cómo declarar y utilizar las clases de vista de registros y de conjunto de registros, vea “Diseñar y crear una vista de registros” en el artículo [Grabe las vistas](../../data/record-views-mfc-data-access.md).  Para obtener más información sobre cómo funcionan las vistas de registros y cómo utilizarlos, vea el artículo [Utilizar una vista de registros](../../data/using-a-record-view-mfc-data-access.md).  Todos los casos mencionados anteriormente se aplican a `CRecordView` y a `CDaoRecordView`.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CDaoRecordView`  
  
## Requisitos  
 **encabezado:** afxdao.h  
  
## Vea también  
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset Class](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)