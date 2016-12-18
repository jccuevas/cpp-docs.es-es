---
title: "CMFCStandardColorsPropertyPage Class | Microsoft Docs"
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
  - "CMFCStandardColorsPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCStandardColorsPropertyPage class"
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCStandardColorsPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una página de propiedades que los usuarios utilicen los colores estándar seleccionar en un cuadro de diálogo color.  
  
## Sintaxis  
  
```  
class CMFCStandardColorsPropertyPage : public CPropertyPage  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCStandardColorsPropertyPage::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCStandardColorsPropertyPage::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
  
### Comentarios  
 La clase de `CMFCColorDialog` utiliza esta clase para mostrar la página de propiedades de color estándar.  Para obtener más información sobre `CMFCColorDialog`, vea [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)  
  
## Requisitos  
 **encabezado:** afxstandardcolorspropertypage.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCCustomColorsPropertyPage Class](../../mfc/reference/cmfccustomcolorspropertypage-class.md)