---
title: "CWinFormsView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinFormsView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinFormsView class"
  - "MFC [C++], compatibilidad con formularios Windows Forms"
  - "formularios Windows Forms [C++], compatibilidad con MFC"
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CWinFormsView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad genérica para hospedar un control de formularios Windows Forms como vista MFC.  
  
## Sintaxis  
  
```  
class CWinFormsView : public CView;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinFormsView::CWinFormsView](../Topic/CWinFormsView::CWinFormsView.md)|Crea un objeto `CWinFormsView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinFormsView::GetControl](../Topic/CWinFormsView::GetControl.md)|Recupera un puntero al control de Windows Forms.|  
  
### Operadores públicos  
  
|Name||  
|----------|-|  
|[CWinFormsView::operator Control^](../Topic/CWinFormsView::operator%20Control%5E.md)|Convierte un tipo como un puntero a un control de formularios Windows Forms.|  
  
## Comentarios  
 MFC utiliza la clase de `CWinFormsView` para hospedar los formularios Windows Forms de .NET Framework controla dentro de una vista MFC.  El control es un elemento secundario de la vista nativa y ocupa toda el área de cliente de la vista MFC.  El resultado es similar a una vista de `CFormView` , lo que se actualicen de formularios Windows Forms diseñador y tiempo de ejecución de crear vistas basadas en formulario enriquecidas.  
  
 Para obtener más información sobre cómo utilizar los formularios Windows Forms, vea [Utilizar un control de usuario de Windows Forms en MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
> [!NOTE]
>  La integración de formularios Windows Forms de MFC sólo funciona en proyectos que se vinculen dinámicamente a MFC \(proyectos en los que AFXDLL es definido\).  
  
> [!NOTE]
>  CWinFormsView no admite la ventana divisora de MFC \([CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)\).  Solo el control splitter de Windows Forms \(<xref:System.Windows.Forms.Splitter>\) se admite actualmente.  
  
## Requisitos  
 **encabezado:** afxwinforms.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWinFormsControl Class](../../mfc/reference/cwinformscontrol-class.md)   
 [CWinFormsDialog Class](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)