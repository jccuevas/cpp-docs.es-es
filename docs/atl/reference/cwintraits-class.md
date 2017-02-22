---
title: "CWinTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinTraits"
  - "CMDIChildWinTraits"
  - "ATL.CWinTraits"
  - "CFrameWinTraits"
  - "ATL::CWinTraits"
  - "CControlWinTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CControlWinTraits class"
  - "CFrameWinTraits class"
  - "CMDIChildWinTraits class"
  - "CWinTraits class"
  - "window styles, default values for ATL"
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CWinTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona un método para normalizar los estilos utilizados al crear un objeto de la ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
DWORD t_dwStyle= 0,  
DWORD t_dwExStyle= 0  
>  
class CWinTraits  
```  
  
#### Parámetros  
 `t_dwStyle`  
 Estilos de ventana estándar predeterminadas.  
  
 `t_dwExStyle`  
 Establezca como valor predeterminado los estilos de ventana extendidas.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](../Topic/CWinTraits::GetWndExStyle.md)|\(Estático\) recupera los estilos extendidos para el objeto de `CWinTraits` .|  
|[CWinTraits::GetWndStyle](../Topic/CWinTraits::GetWndStyle.md)|\(Estático\) recupera los estilos estándar para el objeto de `CWinTraits` .|  
  
## Comentarios  
 Esta clase de [rasgos de la ventana](../../atl/understanding-window-traits.md) proporciona un método simple para normalizar los estilos utilizados para la creación de un objeto de la ventana de ATL.  Utilice una especialización de esta clase como un parámetro de plantilla a [CWindowImpl](../../atl/reference/cwindowimpl-class.md) u otro de las clases de ventana ATL para especificar el estándar predeterminada y los estilos extendidos utilizados para las instancias de esta clase de ventana.  
  
 Utilice esta plantilla cuando se desea proporcionar los estilos de ventana predeterminadas que se usarán cuando no se especifica ningún otros estilos en la llamada a [CWindowImpl:: Crear](../Topic/CWindowImpl::Create.md).  
  
 ATL proporciona tres especializaciones predefinidas de esta plantilla para combinaciones de uso general de estilos de ventana:  
  
 `CControlWinTraits`  
 diseñado para una ventana de control estándar.  Se utilizan los estilos estándar siguientes: **WS\_CHILD**, **WS\_VISIBLE**, **WS\_CLIPCHILDREN**, y **WS\_CLIPSIBLINGS**.  no hay estilos extendidos.  
  
 `CFrameWinTraits`  
 Diseñado para una ventana de marco estándar.  Inclusión utilizada estilos estándar: **WS\_OVERLAPPEDWINDOW**, **WS\_CLIPCHILDREN**, y **WS\_CLIPSIBLINGS**.  Inclusión utilizada estilos extendidos: **WS\_EX\_APPWINDOW** y **WS\_EX\_WINDOWEDGE**.  
  
 `CMDIChildWinTraits`  
 diseñado para una ventana secundaria estándar de MDI.  Inclusión utilizada estilos estándar: **WS\_OVERLAPPEDWINDOW**, **WS\_CHILD**, **WS\_VISIBLE**, **WS\_CLIPCHILDREN**, y **WS\_CLIPSIBLINGS**.  Inclusión utilizada estilos extendidos: **WS\_EX\_MDICHILD**.  
  
 Si desea asegurarse de que ciertos estilos están establecidos para todas las instancias de la clase de ventana mientras permiten otros estilos están establecidos en una base de por instancia, utilice [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) en su lugar.  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [Class Members](http://msdn.microsoft.com/es-es/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Understanding Window Traits](../../atl/understanding-window-traits.md)