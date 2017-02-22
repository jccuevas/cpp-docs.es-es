---
title: "CMFCAcceleratorKeyAssignCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCAcceleratorKeyAssignCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAcceleratorKeyAssignCtrl class"
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCAcceleratorKeyAssignCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCAcceleratorKeyAssignCtrl` amplía la [CEdit Class](../../mfc/reference/cedit-class.md) a fin de ofrecer compatibilidad con teclas adicionales del sistema, como ALT, CONTROL y MAYÚSCULAS.  
  
## Sintaxis  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](../Topic/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl.md)|Construye un objeto `CMFCAcceleratorKeyAssignCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](../Topic/CMFCAcceleratorKeyAssignCtrl::GetAccel.md)|Recupera la estructura `ACCEL` para una tecla de método abreviado pulsada en el objeto `CMFCAcceleratorKeyAssignCtrl`.|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](../Topic/CMFCAcceleratorKeyAssignCtrl::IsFocused.md)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](../Topic/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined.md)|Determina si se ha definido una tecla de método abreviado.|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](../Topic/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage.md)|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).  \(Invalida [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)\).|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](../Topic/CMFCAcceleratorKeyAssignCtrl::ResetKey.md)|Restablece la tecla de método abreviado.|  
  
## Comentarios  
 Esta clase extiende la funcionalidad de la clase `CEdit` ofreciendo compatibilidad con teclas de método abreviado, también conocido como teclas de aceleración.  La clase `CMFCAcceleratorKeyAssignCtrl` funciona como una [CEdit Class](../../mfc/reference/cedit-class.md) y también puede reconocer teclas del sistema.  
  
 Esta clase asigna combinaciones de teclas físicas de método abreviado a valores de cadena.  Por ejemplo, suponga que la combinación de teclas ALT \+ B se asigna a la cadena "Alt \+ B".  Cuando el usuario presione esta combinación de teclas en un objeto `CMFCAcceleratorKeyAssignCtrl`, se le mostrará "Alt \+ B".  Para obtener más información acerca de la asignación de teclas de método abreviado y un formato de cadena, vea el tema sobre la [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto `CMFCAcceleratorKeyAssignCtrl` y utilizar su método `ResetKey` para restablecer la tecla de método abreviado.  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/CPP/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)  
  
## Requisitos  
 **Encabezado:** afxacceleratorkeyassignctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md)