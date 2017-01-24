---
title: "CFormView Class | Microsoft Docs"
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
  - "CFormView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFormView class"
  - "form views"
  - "vistas, containing controls"
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFormView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base utilizada para las vistas de formulario.  
  
## Sintaxis  
  
```  
class CFormView : public CScrollView  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFormView::CFormView](../Topic/CFormView::CFormView.md)|Construye un objeto `CFormView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFormView::IsInitDlgCompleted](../Topic/CFormView::IsInitDlgCompleted.md)|Se usa para la sincronización durante la inicialización.|  
  
## Comentarios  
 Una vista de formulario es esencialmente una vista que contiene controles  que se disponen en función de un recurso de plantilla de cuadro de diálogo.  Use `CFormView` si quiere usar formularios en la aplicación.  Estas vistas admiten el desplazamiento, según sea necesario, con las funciones [CScrollView](../../mfc/reference/cscrollview-class.md).  
  
 Cuando [cree una aplicación basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md), puede basar la clase de vista en `CFormView`, lo que la convierte en una aplicación basada en formularios.  
  
 También puede insertar [temas de formulario](../../mfc/form-views-mfc.md) nuevos en aplicaciones basadas en la vista de documento.  Aunque la aplicación no admitía formularios inicialmente, Visual C\+\+ agregará automáticamente esta compatibilidad al insertar un formulario nuevo.  
  
 El Asistente para aplicaciones MFC y el comando Agregar clase son los métodos preferidos para crear aplicaciones basadas en formularios.  Si necesita crear una aplicación basada en formularios sin usar estos métodos, vea [Crear una aplicación basada en formularios](../../mfc/reference/creating-a-forms-based-mfc-application.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 `CFormView`  
  
## Requisitos  
 **Encabezado:** afxext.h  
  
## Vea también  
 [Ejemplo SNAPVW de MFC](../../top/visual-cpp-samples.md)   
 [Ejemplo VIEWEX de MFC](../../top/visual-cpp-samples.md)   
 [CScrollView Class](../../mfc/reference/cscrollview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [CScrollView Class](../../mfc/reference/cscrollview-class.md)   
 [CView::OnUpdate](../Topic/CView::OnUpdate.md)   
 [CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)   
 [CView::OnPrint](../Topic/CView::OnPrint.md)   
 [CWnd::UpdateData](../Topic/CWnd::UpdateData.md)   
 [CScrollView::ResizeParentToFit](../Topic/CScrollView::ResizeParentToFit.md)