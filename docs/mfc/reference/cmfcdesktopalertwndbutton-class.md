---
title: "CMFCDesktopAlertWndButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDesktopAlertWndButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertWndButton class"
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMFCDesktopAlertWndButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite que los botones se agregan a un cuadro de diálogo de alerta de escritorio.  
  
## Sintaxis  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Constructor predeterminado.|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](../Topic/CMFCDesktopAlertWndButton::IsCaptionButton.md)|Determina si el botón se muestra en el área de leyenda del cuadro de diálogo de alerta.|  
|[CMFCDesktopAlertWndButton::IsCloseButton](../Topic/CMFCDesktopAlertWndButton::IsCloseButton.md)|Determina si se cierra el botón el cuadro de diálogo de alerta.|  
  
### miembros de datos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Valor booleano que especifica si el botón se muestra en el área de leyenda del cuadro de diálogo de alerta.|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Valor booleano que especifica si se cierra el botón el cuadro de diálogo de alerta.|  
  
### Comentarios  
 De forma predeterminada, el constructor establece los miembros de datos de `m_bIsCaptionButton` y de `m_bIsCloseButton` a `FALSE`.  El objeto de `CMFCDesktopAlertDialog` primario establece `m_bIsCaptionButton` a `TRUE` si el botón se coloca en el área de leyenda del cuadro de diálogo de alerta.  La clase de `CMFCDesktopAlertDialog` crea un objeto de `CMFCDesktopAlertWndButton` que actúa como el botón que cierre el cuadro de diálogo de alerta y establece `m_bIsCloseButton` a `TRUE`.  
  
 Agregue los objetos de `CMFCDesktopAlertWndButton` a un objeto de `CMFCDesktopAlertDialog` como agregaría cualquier botón.  Para obtener más información sobre `CMFCDesktopAlertDialog`, vea [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el método de `SetImage` en la clase de `CMFCDesktopAlertWndButton` .  Este fragmento de código es parte de [Ejemplo de demostración de alerta de escritorio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/CPP/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## Requisitos  
 **encabezado:** afxdesktopalertwnd.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)