---
title: "CMFCRibbonCustomizeDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "GetThisClass"
  - "CMFCRibbonCustomizeDialog"
  - "~CMFCRibbonCustomizeDialog"
  - "CMFCRibbonCustomizeDialog::GetThisClass"
  - "CMFCRibbonCustomizeDialog.~CMFCRibbonCustomizeDialog"
  - "CMFCRibbonCustomizeDialog.GetThisClass"
  - "CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCRibbonCustomizeDialog destructor"
  - "CMFCRibbonCustomizeDialog class"
  - "CMFCRibbonCustomizeDialog class, destructor"
  - "GetThisClass method"
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCRibbonCustomizeDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Muestra la página de **Personalizar** ribbon.  
  
## Sintaxis  
  
```  
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](../Topic/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog.md)|Crea un objeto `CMFCRibbonCustomizeDialog`.|  
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonCustomizeDialog::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
  
## Comentarios  
 MFC crea instancias de esta clase automáticamente si no procesa el mensaje de AFX\_WM\_ON\_RIBBON\_CUSTOMIZE, o si devuelve 0 del controlador de mensajes.  
  
 Si desea utilizar esta clase en la aplicación para mostrar el cuadro de diálogo de **Personalizar** ribbon, solo debe hacerse instancias y llame al método de `DoModal` .  
  
 Dado que esta clase es derivada de [CMFCPropertySheet Class](../../mfc/reference/cmfcpropertysheet-class.md), puede agregar páginas personalizadas mediante `CMFCPropertySheet` API.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
 [CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)  
  
## Requisitos  
 **encabezado:** afxribboncustomizedialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)