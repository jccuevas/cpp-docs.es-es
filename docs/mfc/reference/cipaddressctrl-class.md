---
title: "CIPAddressCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CIPAddressCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIPAddressCtrl class"
  - "controles comunes, Internet Explorer 4.0"
  - "Internet address edit box"
  - "Internet Explorer 4.0 common controls"
  - "Internet protocol address box"
  - "IP address control"
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CIPAddressCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control común de la dirección IP de Windows.  
  
## Sintaxis  
  
```  
class CIPAddressCtrl : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CIPAddressCtrl::CIPAddressCtrl](../Topic/CIPAddressCtrl::CIPAddressCtrl.md)|Crea un objeto `CIPAddressCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CIPAddressCtrl::ClearAddress](../Topic/CIPAddressCtrl::ClearAddress.md)|Borra el contenido del Control de dirección IP.|  
|[CIPAddressCtrl::Create](../Topic/CIPAddressCtrl::Create.md)|Crea un Control de la dirección IP y la asocia a un objeto de `CIPAddressCtrl` .|  
|[CIPAddressCtrl::CreateEx](../Topic/CIPAddressCtrl::CreateEx.md)|Crea una dirección IP que el control con Windows especificado extendidas los estilos y la asocia a un objeto de `CIPAddressCtrl` .|  
|[CIPAddressCtrl::GetAddress](../Topic/CIPAddressCtrl::GetAddress.md)|Recupera los valores de dirección para los cuatro campos en el Control de dirección IP.|  
|[CIPAddressCtrl::IsBlank](../Topic/CIPAddressCtrl::IsBlank.md)|Determina si todos los campos en el Control de dirección IP están vacíos.|  
|[CIPAddressCtrl::SetAddress](../Topic/CIPAddressCtrl::SetAddress.md)|Establece los valores de dirección para los cuatro campos en el Control de dirección IP.|  
|[CIPAddressCtrl::SetFieldFocus](../Topic/CIPAddressCtrl::SetFieldFocus.md)|Establece el foco de teclado al campo especificado en el Control de dirección IP.|  
|[CIPAddressCtrl::SetFieldRange](../Topic/CIPAddressCtrl::SetFieldRange.md)|Establece el intervalo en el campo especificado en el Control de dirección IP.|  
  
## Comentarios  
 Un control de la dirección IP, un control similar a un control de edición, permite que se entra y manipular una dirección numérica en formato \(IP\) de protocolo de Internet.  
  
 Este control \(y por consiguiente la clase de `CIPAddressCtrl` \) sólo está disponible para los programas que se ejecutan en Microsoft Internet Explorer 4,0 o posterior.  También estarán disponibles en las versiones de Windows futuras y Windows NT.  
  
 Para obtener más información general sobre el Control de dirección IP, vea [Controles de dirección IP](http://msdn.microsoft.com/library/windows/desktop/bb761372) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)