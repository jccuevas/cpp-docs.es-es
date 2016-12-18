---
title: "CMFCRibbonCustomizePropertyPage Class | Microsoft Docs"
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
  - "CMFCRibbonCustomizePropertyPage::CreateObject"
  - "CMFCRibbonCustomizePropertyPage"
  - "CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage"
  - "CMFCRibbonCustomizePropertyPage.GetThisClass"
  - "CMFCRibbonCustomizePropertyPage.CreateObject"
  - "~CMFCRibbonCustomizePropertyPage"
  - "CreateObject"
  - "CMFCRibbonCustomizePropertyPage.~CMFCRibbonCustomizePropertyPage"
  - "CMFCRibbonCustomizePropertyPage::GetThisClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCRibbonCustomizePropertyPage destructor"
  - "CMFCRibbonCustomizePropertyPage class"
  - "CMFCRibbonCustomizePropertyPage class, destructor"
  - "CreateObject method"
  - "GetThisClass method"
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonCustomizePropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

implementa una página personalizada para el cuadro de diálogo de **Personalizar** en aplicaciones Cinta de opciones\-basadas.  
  
## Sintaxis  
  
```  
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](../Topic/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage.md)|Crea un objeto `CMFCRibbonCustomizePropertyPage`.|  
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](../Topic/CMFCRibbonCustomizePropertyPage::AddCustomCategory.md)|Agrega una categoría personalizada al cuadro combinado de Commandos.|  
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCRibbonCustomizePropertyPage::OnOK](../Topic/CMFCRibbonCustomizePropertyPage::OnOK.md)|Llamado por el sistema cuando un usuario hace clic en **Aceptar** en el cuadro de diálogo de **Personalizar** .|  
  
## Comentarios  
 Si desea agregar comandos personalizados al cuadro de diálogo de **Personalizar** , debe controlar el mensaje de AFX\_WM\_ON\_RIBBON\_CUSTOMIZE.  En el controlador de mensajes, cree instancias de un objeto de `CMFCRibbonCustomizePropertyPage` en la pila.  Cree una lista de comandos personalizados, y llame a `AddCustomCategory` para agregar la nueva página al cuadro de diálogo de **Personalizar** .  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de `CMFCRibbonCustomizePropertyPage` y agregar una categoría personalizada.  
  
 [!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/CPP/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
 [CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)  
  
## Requisitos  
 **encabezado:** afxribboncustomizedialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)