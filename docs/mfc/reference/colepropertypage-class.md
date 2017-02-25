---
title: "COlePropertyPage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COlePropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COlePropertyPage class"
  - "controles personalizados [MFC], propiedades"
  - "displaying properties"
  - "OLE property pages"
  - "propiedades [C++], mostrar"
  - "páginas de propiedades, OLE"
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COlePropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se usa para mostrar las propiedades de un control personalizado en una interfaz gráfica, a un cuadro de diálogo.  
  
## Sintaxis  
  
```  
class AFX_NOVTABLE COlePropertyPage : public CDialog  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePropertyPage::COlePropertyPage](../Topic/COlePropertyPage::COlePropertyPage.md)|Crea un objeto `COlePropertyPage`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COlePropertyPage::GetControlStatus](../Topic/COlePropertyPage::GetControlStatus.md)|Indica si el usuario ha modificado el valor del control.|  
|[COlePropertyPage::GetObjectArray](../Topic/COlePropertyPage::GetObjectArray.md)|Devuelve la matriz de objetos que son modificados por la página de propiedades.|  
|[COlePropertyPage::GetPageSite](../Topic/COlePropertyPage::GetPageSite.md)|devuelve un puntero a la interfaz de `IPropertyPageSite` de la página de propiedades.|  
|[COlePropertyPage::IgnoreApply](../Topic/COlePropertyPage::IgnoreApply.md)|Determina que controla no habilita el botón de aplicar.|  
|[COlePropertyPage::IsModified](../Topic/COlePropertyPage::IsModified.md)|indica si el usuario ha modificado la página de propiedades.|  
|[COlePropertyPage::OnEditProperty](../Topic/COlePropertyPage::OnEditProperty.md)|Llamado por el marco cuando el usuario modifica una propiedad.|  
|[COlePropertyPage::OnHelp](../Topic/COlePropertyPage::OnHelp.md)|Llamado por el marco cuando el usuario invoca ayuda.|  
|[COlePropertyPage::OnInitDialog](../Topic/COlePropertyPage::OnInitDialog.md)|Llamado por el marco cuando se inicializa la página de propiedades.|  
|[COlePropertyPage::OnObjectsChanged](../Topic/COlePropertyPage::OnObjectsChanged.md)|Llamado por el marco cuando otro control OLE, con nuevas propiedades, se elige.|  
|[COlePropertyPage::OnSetPageSite](../Topic/COlePropertyPage::OnSetPageSite.md)|Llamado por el marco cuando el cuadro de la propiedad proporciona el sitio de la página.|  
|[COlePropertyPage::SetControlStatus](../Topic/COlePropertyPage::SetControlStatus.md)|Establece una marca que indica si el usuario ha modificado el valor del control.|  
|[COlePropertyPage::SetDialogResource](../Topic/COlePropertyPage::SetDialogResource.md)|Establece el recurso de diálogo página de propiedades.|  
|[COlePropertyPage::SetHelpInfo](../Topic/COlePropertyPage::SetHelpInfo.md)|Establece el texto de ayuda abreviado de la página de propiedades, el nombre del archivo de ayuda, y el contexto de ayuda.|  
|[COlePropertyPage::SetModifiedFlag](../Topic/COlePropertyPage::SetModifiedFlag.md)|Establece una marca que indica si el usuario ha modificado la página de propiedades.|  
|[COlePropertyPage::SetPageName](../Topic/COlePropertyPage::SetPageName.md)|Establece el nombre de la página de propiedades \(caption\).|  
  
## Comentarios  
 Por ejemplo, una página de propiedades puede incluir un control de edición que permite al usuario ver y modificar la propiedad caption del control.  
  
 Cada propiedad personalizada o control común puede tener un control de cuadro de diálogo que permite al usuario del control vea el valor de propiedad actual y modifique ese valor si es necesario.  
  
 Para obtener más información sobre cómo utilizar `COlePropertyPage`, vea el artículo [Controles ActiveX: Páginas de propiedades](../../mfc/mfc-activex-controls-property-pages.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `COlePropertyPage`  
  
## Requisitos  
 **encabezado:** afxctl.h  
  
## Vea también  
 [ejemplo CIRC3 de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo TESTHELP de MFC](../../top/visual-cpp-samples.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)