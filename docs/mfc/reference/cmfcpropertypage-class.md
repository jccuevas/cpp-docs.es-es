---
title: "CMFCPropertyPage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyPage class"
  - "CMFCPropertyPage::CreateObject method"
  - "CMFCPropertyPage::OnSetActive method"
  - "CMFCPropertyPage::PreTranslateMessage method"
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCPropertyPage` admite la presentación de menús emergentes en una página de propiedades.  
  
## Sintaxis  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyPage::CMFCPropertyPage](../Topic/CMFCPropertyPage::CMFCPropertyPage.md)|Crea un objeto `CMFCPropertyPage`.|  
|`CMFCPropertyPage::~CMFCPropertyPage`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCPropertyPage::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCPropertyPage::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|`CMFCPropertyPage::OnSetActive`|Esta función miembro llaman el marco cuando ésta se elegida por el usuario y se convierte en la página activa.  \(Reemplaza [CPropertyPage::OnSetActive](../Topic/CPropertyPage::OnSetActive.md).\)|  
|`CMFCPropertyPage::PreTranslateMessage`|Traduce mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  Para obtener más sintaxis de información y de método, vea [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).  \(Reemplaza `CPropertyPage::PreTranslateMessage`.\)|  
  
## Comentarios  
 la clase de `CMFCPropertyPage` representa las páginas individuales de una hoja de propiedades, si no conocidas como cuadro de diálogo de la ficha.  
  
 utilice la clase de `CMFCPropertyPage` así como la clase de [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) .  Para usar los menús de una página de propiedades, reemplace todas las apariciones de la clase de `CPropertyPage` con la clase de `CMFCPropertyPage` .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## Requisitos  
 **encabezado:** afxpropertypage.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertySheet Class](../../mfc/reference/cmfcpropertysheet-class.md)