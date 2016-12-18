---
title: "CMFCMenuButton (clase) | Microsoft Docs"
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
  - "CMFCMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCMenuButton (clase)"
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
caps.latest.revision: 32
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCMenuButton (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un botón que muestra un menú emergente y informes en las selecciones de menú del usuario.  
  
## Sintaxis  
  
```  
class CMFCMenuButton : public CMFCButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCMenuButton::CMFCMenuButton](../Topic/CMFCMenuButton::CMFCMenuButton.md)|Crea un objeto `CMFCMenuButton`.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCMenuButton::PreTranslateMessage](../Topic/CMFCMenuButton::PreTranslateMessage.md)|Llamado por el marco para traducir mensajes de ventana antes de que se envíen.  \(Reemplaza `CMFCButton::PreTranslateMessage`.\)|  
|[CMFCMenuButton::SizeToContent](../Topic/CMFCMenuButton::SizeToContent.md)|Cambia el tamaño del botón según su texto y tamaño de la imagen.|  
  
### Miembros de datos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCMenuButton::m\_bOSMenu](../Topic/CMFCMenuButton::m_bOSMenu.md)|Especifica si mostrar el menú emergente del sistema predeterminada o utilizar [CContextMenuManager::TrackPopupMenu](../Topic/CContextMenuManager::TrackPopupMenu.md).|  
|[CMFCMenuButton::m\_bRightArrow](../Topic/CMFCMenuButton::m_bRightArrow.md)|Especifica bajo si el menú emergente aparecerá o a la derecha del botón.|  
|[CMFCMenuButton::m\_bStayPressed](../Topic/CMFCMenuButton::m_bStayPressed.md)|Especifica si el botón de menú cambia su estado después del usuario suelta el botón.|  
|[CMFCMenuButton::m\_hMenu](../Topic/CMFCMenuButton::m_hMenu.md)|Un identificador al menú de Windows asociado.|  
|[CMFCMenuButton::m\_nMenuResult](../Topic/CMFCMenuButton::m_nMenuResult.md)|Un identificador que indica qué elemento seleccionado el usuario del elemento emergente.|  
  
## Comentarios  
 La clase de `CMFCMenuButton` se deriva de [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md) que, a su vez, se deriva de [CButton Class](../../mfc/reference/cbutton-class.md).  Por consiguiente, puede utilizar `CMFCMenuButton` en el código de la misma manera que utilizaría `CButton`.  
  
 Cuando se crea `CMFCMenuButton`, debe pasar un identificador al menú emergente asociado.  A continuación, llama a la función `CMFCMenuButton::SizeToContent`.  comprobaciones de `CMFCMenuButton::SizeToContent` que el tamaño del botón es suficiente para incluir una flecha que apunta a la ubicación donde aparecerá la ventana emergente \(concretamente, debajo o a la derecha del botón.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo establecer el identificador de menú asociado al botón, cambia el tamaño del botón según su texto y tamaño de imagen, y establece el menú emergente que muestra el marco.  Este fragmento de código es parte de [Nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/CPP/cmfcmenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/CPP/cmfcmenubutton-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)  
  
## Requisitos  
 **Encabezado:** afxmenubutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md)