---
title: "COleDispatchDriver Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDispatchDriver"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation clients, implementing Automation"
  - "COleDispatchDriver class"
  - "OLE dispatch interface"
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# COleDispatchDriver Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa el cliente de automatización OLE.  
  
## Sintaxis  
  
```  
class COleDispatchDriver  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDispatchDriver::COleDispatchDriver](../Topic/COleDispatchDriver::COleDispatchDriver.md)|Crea un objeto `COleDispatchDriver`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDispatchDriver::AttachDispatch](../Topic/COleDispatchDriver::AttachDispatch.md)|Adjunta una conexión de `IDispatch` al objeto de `COleDispatchDriver` .|  
|[COleDispatchDriver::CreateDispatch](../Topic/COleDispatchDriver::CreateDispatch.md)|Crea una conexión de `IDispatch` y la agrega al objeto de `COleDispatchDriver` .|  
|[COleDispatchDriver::DetachDispatch](../Topic/COleDispatchDriver::DetachDispatch.md)|Desasocia una conexión de `IDispatch` , sin que el mercadola.|  
|[COleDispatchDriver::GetProperty](../Topic/COleDispatchDriver::GetProperty.md)|Obtiene una propiedad de automatización.|  
|[COleDispatchDriver::InvokeHelper](../Topic/COleDispatchDriver::InvokeHelper.md)|Aplicación auxiliar para llamar a métodos de automatización.|  
|[COleDispatchDriver::ReleaseDispatch](../Topic/COleDispatchDriver::ReleaseDispatch.md)|Libera una conexión de `IDispatch` .|  
|[COleDispatchDriver::SetProperty](../Topic/COleDispatchDriver::SetProperty.md)|Establece una propiedad de automatización.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDispatchDriver::operator \=](../Topic/COleDispatchDriver::operator%20=.md)|Copia el valor de origen en el objeto de `COleDispatchDriver` .|  
|[COleDispatchDriver::operator LPDISPATCH](../Topic/COleDispatchDriver::operator%20LPDISPATCH.md)|Tiene acceso al puntero subyacente de `IDispatch` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDispatchDriver::m\_bAutoRelease](../Topic/COleDispatchDriver::m_bAutoRelease.md)|Especifica si liberar `IDispatch` durante `ReleaseDispatch` u oponerse destrucción.|  
|[COleDispatchDriver::m\_lpDispatch](../Topic/COleDispatchDriver::m_lpDispatch.md)|Indica el puntero a la interfaz de `IDispatch` asociada a este `COleDispatchDriver`.|  
  
## Comentarios  
 `COleDispatchDriver` no tiene una clase base.  
  
 Las interfaces de distribución VIEJAS proporcionan acceso a los métodos y las propiedades de un objeto.  Las funciones miembro de `COleDispatchDriver` asociado, desasociar, crean, y se liberan una conexión de envío de `IDispatch`escrito.  Otras funciones miembro utilizan listas de argumentos variables para simplificar llamar **IDispatch::Invoke**.  
  
 Esta clase se puede utilizar directamente, pero se suele utilizar sólo las clases creadas por el asistente de la clase add.  Cuando se crea un nuevo C\+\+ ordena importando una biblioteca de tipos, las nuevas clases se deriva de `COleDispatchDriver`.  
  
 Para obtener más información sobre cómo utilizar `COleDispatchDriver`, vea los artículos siguientes:  
  
-   [Clientes de automatización](../../mfc/automation-clients.md)  
  
-   [Servidores de automatización](../../mfc/automation-servers.md)  
  
## Jerarquía de herencia  
 `COleDispatchDriver`  
  
## Requisitos  
 **encabezado:** afxdisp.h  
  
## Vea también  
 [ejemplo CALCDRIV de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo ACDUAL de MFC](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)