---
title: "CWinTraitsOR Class | Microsoft Docs"
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
  - "ATL.CWinTraitsOR"
  - "ATL::CWinTraitsOR"
  - "CWinTraitsOR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinTraitsOR class"
  - "window styles, default values for ATL"
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinTraitsOR Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona un método para normalizar los estilos utilizados al crear un objeto de la ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
DWORD t_dwStyle= 0,  
DWORDt_dwExStyle= 0,  
class TWinTraits = CControlWinTraits   
>  
class CWinTraitsOR  
```  
  
#### Parámetros  
 `t_dwStyle`  
 Estilos de ventana predeterminadas.  
  
 `t_dwExStyle`  
 Establezca como valor predeterminado los estilos de ventana extendidas.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](../Topic/CWinTraitsOR::GetWndExStyle.md)|Recupera los estilos extendidos para el objeto de `CWinTraitsOR` .|  
|[CWinTraitsOR::GetWndStyle](../Topic/CWinTraitsOR::GetWndStyle.md)|Recupera los estilos estándar para el objeto de `CWinTraitsOR` .|  
  
## Comentarios  
 Esta clase de [rasgos de la ventana](../../atl/understanding-window-traits.md) proporciona un método simple para normalizar los estilos utilizados para la creación de un objeto de la ventana de ATL.  Utilice una especialización de esta clase como un parámetro de plantilla a [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otro de las clases de ventana ATL para especificar el conjunto mínimo de standard y los estilos extendidos que se utilizarán para las instancias de esta clase de ventana.  
  
 Utilice una especialización de esta plantilla si desea garantizar que ciertos estilos están establecidos para todas las instancias de la clase de ventana mientras permiten otros estilos están establecidos en función de la por\- instancia en la llamada a [CWindowImpl::Create](../Topic/CWindowImpl::Create.md).  
  
 Si desea proporcionar los estilos de ventana predeterminadas que se usarán cuando no se especifica ningún otros estilos en la llamada a `CWindowImpl::Create`, utilice [CWinTraits](../../atl/reference/cwintraits-class.md) en su lugar.  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Understanding Window Traits](../../atl/understanding-window-traits.md)