---
title: "CSplitButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSplitButton class"
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CSplitButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CSplitButton` representa un control de botón de expansión.  El control de botón de expansión realiza un comportamiento predeterminado cuando un usuario hace clic en la parte principal del botón, y muestra un menú desplegable cuando un usuario hace clic en la flecha de lista desplegable del botón.  
  
## Sintaxis  
  
```  
class CSplitButton : public CButton  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSplitButton::CSplitButton](../Topic/CSplitButton::CSplitButton.md)|Crea un objeto `CSplitButton`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSplitButton::Create](../Topic/CSplitButton::Create.md)|Crea un control de botón de expansión con estilos especificados y lo asocia al objeto actual de `CSplitButton` .|  
|[CSplitButton::SetDropDownMenu](../Topic/CSplitButton::SetDropDownMenu.md)|Establece el menú desplegable que se muestra cuando un usuario hace clic en la flecha de lista desplegable del control actual de botón de expansión.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSplitButton::OnDropDown](../Topic/CSplitButton::OnDropDown.md)|Controla la notificación de `BCN_DROPDOWN` que el sistema envía cuando un usuario hace clic en la flecha de lista desplegable del control actual de botón de expansión.|  
  
## Comentarios  
 la clase de `CSplitButton` es derivada de la clase de [CButton](../../mfc/reference/cbutton-class.md) .  El control de botón de expansión es un control de botón cuyo estilo es `BS_SPLITBUTTON`.  Muestra un menú personalizado cuando un usuario hace clic en la flecha de lista desplegable.  Para obtener más información, vea estilos de `BS_SPLITBUTTON` y de `BS_DEFSPLITBUTTON` en [estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb775951).  
  
 La ilustración siguiente describe un cuadro de diálogo que contiene un control de paginación y \(1\) un control de botón de expansión.  \(2\) La flecha de lista desplegable se ha hecho clic ya y \(3\) se muestra el submenú.  
  
 ![Cuadro de diálogo con botón de división y control de paginación.](../../mfc/reference/media/splitbutton_pager.png "SplitButton\_Pager")  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
 Esta clase se admite en [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] y posterior.  
  
 los requisitos adicionales para esta clase se describen en [Requisitos de compilación para los controles comunes de Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).  
  
## Vea también  
 [CSplitButton Class](../../mfc/reference/csplitbutton-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)