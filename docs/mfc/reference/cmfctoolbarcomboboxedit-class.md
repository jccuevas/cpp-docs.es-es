---
title: "CMFCToolBarComboBoxEdit Class | Microsoft Docs"
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
  - "CMFCComboEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarComboBoxEdit class"
  - "CMFCToolBarComboBoxEdit::PreTranslateMessage method"
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
caps.latest.revision: 25
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarComboBoxEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El marco de trabajo usa la clase de `CMFCToolBarComboBoxEdit` para crear un botón de la barra de herramientas que se comporte como un control modificable del cuadro combinado.  
  
## Sintaxis  
  
```  
class CMFCToolBarComboBoxEdit : public CEdit  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](../Topic/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit.md)|Crea un objeto `CMFCToolBarComboBoxEdit`.|  
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|Traduce mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  \(Reemplaza [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).\)|  
  
### Comentarios  
 Derive una clase de la clase de `CMFCToolBarComboBoxEdit` para personalizar las operaciones de edición.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbarcomboboxbutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarComboBoxButton::CreateEdit](../Topic/CMFCToolBarComboBoxButton::CreateEdit.md)