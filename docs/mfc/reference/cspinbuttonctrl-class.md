---
title: "CSpinButtonCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSpinButtonCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSpinButtonCtrl class"
  - "CSpinButtonCtrl class, controles comunes"
  - "control de botón de número"
  - "controles de flechas, control de botón de número"
  - "Windows common controls [C++], CSpinButtonCtrl"
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CSpinButtonCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control de botón común de retorno de Windows.  
  
## Sintaxis  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](../Topic/CSpinButtonCtrl::CSpinButtonCtrl.md)|Crea un objeto `CSpinButtonCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSpinButtonCtrl::Create](../Topic/CSpinButtonCtrl::Create.md)|Crea un control de botón de número y lo asocia a un objeto de `CSpinButtonCtrl` .|  
|[CSpinButtonCtrl::CreateEx](../Topic/CSpinButtonCtrl::CreateEx.md)|Crea un control de botón de retorno con Windows especificado extendidas estilos y lo asocia a un objeto de `CSpinButtonCtrl` .|  
|[CSpinButtonCtrl::GetAccel](../Topic/CSpinButtonCtrl::GetAccel.md)|Recupera información de aceleración para un control de botón de número.|  
|[CSpinButtonCtrl::GetBase](../Topic/CSpinButtonCtrl::GetBase.md)|Recupera la base actual para un control de botón de número.|  
|[CSpinButtonCtrl::GetBuddy](../Topic/CSpinButtonCtrl::GetBuddy.md)|Recupera un puntero a la ventana actual de relacionada.|  
|[CSpinButtonCtrl::GetPos](../Topic/CSpinButtonCtrl::GetPos.md)|Recupera la posición actual de un control de botón de número.|  
|[CSpinButtonCtrl::GetRange](../Topic/CSpinButtonCtrl::GetRange.md)|Recupera los límites superior e inferior \(intervalo\) para un control de botón de número.|  
|[CSpinButtonCtrl::SetAccel](../Topic/CSpinButtonCtrl::SetAccel.md)|Establece la aceleración de un control de botón de número.|  
|[CSpinButtonCtrl::SetBase](../Topic/CSpinButtonCtrl::SetBase.md)|Establece la base para un control de botón de número.|  
|[CSpinButtonCtrl::SetBuddy](../Topic/CSpinButtonCtrl::SetBuddy.md)|Establece la ventana de relacionada para un control de botón de número.|  
|[CSpinButtonCtrl::SetPos](../Topic/CSpinButtonCtrl::SetPos.md)|Establece la posición actual del control.|  
|[CSpinButtonCtrl::SetRange](../Topic/CSpinButtonCtrl::SetRange.md)|Establece los límites superior e inferior \(intervalo\) para un control de botón de número.|  
  
## Comentarios  
 Un “control de botón de retorno” \(también conocido como control giratorio\) es un par de botones de flecha que el usuario puede hacer clic para aumentar o reducir un valor, como una posición de desplazamiento o un número mostrado en un control complementarias.  El valor asociado a un control de botón de número se denomina su posición actual.  Un control de botón de retorno es el uso frecuente con un control complementario, denominado un “ventana de relacionada”.  
  
 Este control \(y por consiguiente la clase de `CSpinButtonCtrl` \) sólo está disponible para los programas que se ejecutan en versión 3,51 de Windows 95 \/98 y Windows NT y posterior.  
  
 El usuario, un control de botón de número y su ventana de relacionada parecen a menudo un único control.  Puede especificar que un control de botón de número automáticamente se colocar al lado de la ventana de relacionada, y que establece automáticamente la leyenda de la ventana de relacionada a su posición actual.  Puede utilizar un control de botón de retorno con un control de edición para solicitar al usuario una entrada numérica.  
  
 Haga clic en la flecha arriba mueve la posición actual hacia el máximo, y haciendo clic en la flecha abajo mueve la posición actual hacia el mínimo.  De forma predeterminada, el valor mínimo es 100 y el máximo es 0.  Cualquier momento el valor mínimo es mayor que el valor máximo \(por ejemplo, cuando se utilizan la configuración predeterminada\), haga clic en la flecha arriba reduce el valor de posición y haciendo clic en la flecha abajo la aumenta.  
  
 Un control de botón de número sin funciones de una ventana de relacionada como una especie de la barra de desplazamiento simplificada.  Por ejemplo, un control de la pestaña muestra a veces un control de botón de número para permitir al usuario desplazar pestañas adicionales en la vista.  
  
 Para obtener más información sobre cómo utilizar `CSpinButtonCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [ejemplo CMNCTRL2 de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl Class](../../mfc/reference/csliderctrl-class.md)