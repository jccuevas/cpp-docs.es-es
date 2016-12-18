---
title: "CMFCCustomColorsPropertyPage Class | Microsoft Docs"
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
  - "CMFCCustomColorsPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCustomColorsPropertyPage class"
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCCustomColorsPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una página de propiedades que pueda seleccionar colores personalizados en un cuadro de diálogo color.  
  
## Sintaxis  
  
```  
class CMFCCustomColorsPropertyPage : public CPropertyPage  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCCustomColorsPropertyPage::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCCustomColorsPropertyPage::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCCustomColorsPropertyPage::Setup](../Topic/CMFCCustomColorsPropertyPage::Setup.md)|Establece los componentes de color de la página de propiedades.|  
  
### Comentarios  
 La clase de `CMFCColorDialog` utiliza esta clase para mostrar la página de propiedades color personalizado.  Para obtener más información sobre `CMFCColorDialog`, vea [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de `CMFCCustomColorsPropertyPage` y establecer los componentes de color de la página de propiedades.  
  
 [!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/CPP/cmfccustomcolorspropertypage-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)  
  
## Requisitos  
 **encabezado:** afxcustomcolorspropertypage.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage Class](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)