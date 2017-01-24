---
title: "CMFCRibbonSeparator Class | Microsoft Docs"
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
  - "GetThisClass"
  - "CMFCRibbonSeparator::GetThisClass"
  - "CMFCRibbonSeparator.CreateObject"
  - "CMFCRibbonSeparator::CreateObject"
  - "CMFCRibbonSeparator"
  - "CreateObject"
  - "CMFCRibbonSeparator.GetThisClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonSeparator class"
  - "CreateObject method"
  - "GetThisClass method"
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonSeparator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

implementa el separador de la cinta de opciones.  
  
## Sintaxis  
  
```  
class CMFCRibbonSeparator : public CMFCRibbonBaseElement  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCRibbonSeparator::CMFCRibbonSeparator](../Topic/CMFCRibbonSeparator::CMFCRibbonSeparator.md)|Crea un objeto `CMFCRibbonSeparator`.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCRibbonSeparator::AddToListBox](../Topic/CMFCRibbonSeparator::AddToListBox.md)|Agrega un separador al Commandos mostrado en el cuadro de diálogo de **Personalizar** .  \(Reemplaza [CMFCRibbonBaseElement::AddToListBox](../Topic/CMFCRibbonBaseElement::AddToListBox.md).\)|  
|`CMFCRibbonSeparator::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonSeparator::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
  
### Métodos protegidos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCRibbonSeparator::CopyFrom](../Topic/CMFCRibbonSeparator::CopyFrom.md)|Un método copy a las variables miembro de un separador de otro objeto.|  
|[CMFCRibbonSeparator::GetRegularSize](../Topic/CMFCRibbonSeparator::GetRegularSize.md)|Devuelve el tamaño de un separador.|  
|[CMFCRibbonSeparator::IsSeparator](../Topic/CMFCRibbonSeparator::IsSeparator.md)|Indica si se trata de un separador.|  
|[CMFCRibbonSeparator::IsTabStop](../Topic/CMFCRibbonSeparator::IsTabStop.md)|Indica si se trata de una tabulación.|  
|[CMFCRibbonSeparator::OnDraw](../Topic/CMFCRibbonSeparator::OnDraw.md)|Llamado por el sistema para dibujar el separador en la cinta de opciones o la barra de herramientas de acceso rápido.|  
|[CMFCRibbonSeparator::OnDrawOnList](../Topic/CMFCRibbonSeparator::OnDrawOnList.md)|Llamado por el sistema para dibujar el separador en la lista de Commandos.|  
  
## Comentarios  
 Un separador de la cinta de opciones es una línea vertical u horizontal que separan lógicamente elementos de cinta de opciones.  Un separador se puede dibujar en el control de la cinta de opciones, el menú principal de la aplicación, la barra de estado de la cinta de opciones, y la barra de herramientas de acceso rápido.  
  
 Para utilizar un separador en la aplicación, cree el nuevo objeto y agréguelo al menú principal de la aplicación como se muestra aquí:  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"), IDB_FILESMALL, IDB_FILELARGE);   
...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));  
```  
  
 Llame a [CMFCRibbonPanel::AddSeparator](../Topic/CMFCRibbonPanel::AddSeparator.md) para agregar los separadores en los paneles de la cinta de opciones.  Los separadores son asignados y agregados internamente por el método de `AddSeparator` .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## Requisitos  
 **encabezado:** afxbaseribbonelement.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)