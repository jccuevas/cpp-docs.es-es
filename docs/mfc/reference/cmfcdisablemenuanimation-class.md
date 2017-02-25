---
title: "CMFCDisableMenuAnimation Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDisableMenuAnimation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDisableMenuAnimation class"
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCDisableMenuAnimation Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Deshabilita la animación de menú emergente.  
  
## Sintaxis  
  
```  
class CMFCDisableMenuAnimation  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Crea un objeto `CMFCDisableMenuAnimation`.|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCDisableMenuAnimation::Restore](../Topic/CMFCDisableMenuAnimation::Restore.md)|Restablece la animación anterior que el marco utilizado para mostrar un menú emergente.|  
  
### miembros de datos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCDisableMenuAnimation::m_animType`|Almacena el tipo de animación anterior del elemento emergente.|  
  
### Comentarios  
 Utilice esta clase auxiliar para deshabilitar temporalmente la animación de menú emergente \(por ejemplo, cuando se procesa el mouse o comandos de teclado\).  
  
 Un objeto de `CMFCDisableMenuAnimation` deshabilita la animación de menú emergente durante su duración.  El constructor almacena la animación actual del elemento emergente escriba en el campo de `m_animType` y establezca la animación actual tipo a `CMFCPopupMenu::NO_ANIMATION`.  Destructor restablece el tipo de animación anterior.  
  
 Puede crear un objeto de `CMFCDisableMenuAnimation` en la pila a la animación gris del menú emergente de una sola función.  Si desea deshabilitar la animación de menú emergente entre funciones, cree un objeto de `CMFCDisableMenuAnimation` en la pila y después elimínelo cuando desea restaurar la animación de menú emergente.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar la pila para deshabilitar temporalmente la animación de menú.  
  
 [!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/CPP/cmfcdisablemenuanimation-class_1.h)]  
  
## Jerarquía de herencia  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## Requisitos  
 **encabezado:** afxpopupmenu.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)