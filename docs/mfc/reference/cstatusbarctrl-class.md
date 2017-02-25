---
title: "CStatusBarCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStatusBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBarCtrl class"
  - "status bar controls"
  - "Windows common controls [C++], CStatusBarCtrl"
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CStatusBarCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de controles comunes de la barra de estado de Windows.  
  
## Sintaxis  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStatusBarCtrl::CStatusBarCtrl](../Topic/CStatusBarCtrl::CStatusBarCtrl.md)|Crea un objeto `CStatusBarCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](../Topic/CStatusBarCtrl::Create.md)|Crea un control de barra de estado y se asocia a un objeto de `CStatusBarCtrl` .|  
|[CStatusBarCtrl::CreateEx](../Topic/CStatusBarCtrl::CreateEx.md)|Crea un control de barra de estado con Windows especificado extendidas estilos y lo asocia a un objeto de `CStatusBarCtrl` .|  
|[CStatusBarCtrl::DrawItem](../Topic/CStatusBarCtrl::DrawItem.md)|Llamado cuando un aspecto visual de los cambios de dibujo del propietario de un control de barra de estado.|  
|[CStatusBarCtrl::GetBorders](../Topic/CStatusBarCtrl::GetBorders.md)|Recupera los anchos actuales de los bordes horizontales y verticales de un control de barra de estado.|  
|[CStatusBarCtrl::GetIcon](../Topic/CStatusBarCtrl::GetIcon.md)|Recupera el icono de una parte \(también conocida como panel\) en el control actual de la barra de estado.|  
|[CStatusBarCtrl::GetParts](../Topic/CStatusBarCtrl::GetParts.md)|Recupera un recuento de elementos en un control de barra de estado.|  
|[CStatusBarCtrl::GetRect](../Topic/CStatusBarCtrl::GetRect.md)|Recupera el rectángulo delimitador de elemento en un control de barra de estado.|  
|[CStatusBarCtrl::GetText](../Topic/CStatusBarCtrl::GetText.md)|Recupera el texto de la parte determinada de un control de barra de estado.|  
|[CStatusBarCtrl::GetTextLength](../Topic/CStatusBarCtrl::GetTextLength.md)|Recupere la longitud, en caracteres, de texto de la parte determinada de un control de barra de estado.|  
|[CStatusBarCtrl::GetTipText](../Topic/CStatusBarCtrl::GetTipText.md)|Recupera el texto de información sobre herramientas de un panel en una barra de estado.|  
|[CStatusBarCtrl::IsSimple](../Topic/CStatusBarCtrl::IsSimple.md)|Comprueba un control de la ventana de estado para determinar si está en modo simple.|  
|[CStatusBarCtrl::SetBkColor](../Topic/CStatusBarCtrl::SetBkColor.md)|establece el color de fondo en una barra de estado.|  
|[CStatusBarCtrl::SetIcon](../Topic/CStatusBarCtrl::SetIcon.md)|establece el icono para un panel en una barra de estado.|  
|[CStatusBarCtrl::SetMinHeight](../Topic/CStatusBarCtrl::SetMinHeight.md)|Establece el alto mínimo de área de gráfico de un control de barra de estado.|  
|[CStatusBarCtrl::SetParts](../Topic/CStatusBarCtrl::SetParts.md)|Establece el número de elementos en un control de barra de estado y la coordenada del borde derecho de cada partición.|  
|[CStatusBarCtrl::SetSimple](../Topic/CStatusBarCtrl::SetSimple.md)|Especifica si un control de barra de estado muestra el texto simple o muestra todos los elementos de control establecidos por una llamada anterior a `SetParts`.|  
|[CStatusBarCtrl::SetText](../Topic/CStatusBarCtrl::SetText.md)|Establece el texto en la parte determinada de un control de barra de estado.|  
|[CStatusBarCtrl::SetTipText](../Topic/CStatusBarCtrl::SetTipText.md)|Establece el texto de información sobre herramientas de un panel en una barra de estado.|  
  
## Comentarios  
 Un “control de la barra de estado” es una ventana horizontal, normalmente en la parte inferior de una ventana primaria, donde una aplicación puede mostrar varios tipos de información de estado.  El control de barra de estado se puede dividir en partes para mostrar más de un tipo de información.  
  
 Este control \(y por consiguiente la clase de `CStatusBarCtrl` \) sólo está disponible para los programas que se ejecutan en versión 3,51 de Windows 95 \/98 y Windows NT y posterior.  
  
 Para obtener más información sobre cómo utilizar `CStatusBarCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl Class](../../mfc/reference/ctoolbarctrl-class.md)