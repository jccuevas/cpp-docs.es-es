---
title: "IDispEventSimpleImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDispEventSimpleImpl"
  - "ATL::IDispEventSimpleImpl"
  - "ATL.IDispEventSimpleImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventSimpleImpl class"
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# IDispEventSimpleImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona implementaciones de los métodos de `IDispatch` , sin obtener información de tipo de una biblioteca de tipos.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template <  
UINT nID,  
class T,  
const IID* pdiid  
>  
class ATL_NO_VTABLE IDispEventSimpleImpl :  
public _IDispEventLocator<nID, pdiid>  
```  
  
#### Parámetros  
 `nID`  
 un identificador único para el objeto de origen.  Cuando `IDispEventSimpleImpl` es la clase base para un control compuesto, utilice el Id. de recurso de control contenido deseado para este parámetro.  en otros casos, utilice un entero positivo arbitrario.  
  
 `T`  
 La clase de usuario, que es derivada de `IDispEventSimpleImpl`.  
  
 `pdiid`  
 El puntero al identificador IID dispinterface de evento implementado por esta clase.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispEventSimpleImpl::Advise](../Topic/IDispEventSimpleImpl::Advise.md)|Establece una conexión con el origen de eventos predeterminado.|  
|[IDispEventSimpleImpl::DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md)|establece una conexión con el origen de eventos.|  
|[IDispEventSimpleImpl::DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md)|interrumpe la conexión con el origen de eventos.|  
|[IDispEventSimpleImpl::GetIDsOfNames](../Topic/IDispEventSimpleImpl::GetIDsOfNames.md)|devuelve **E\_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfo](../Topic/IDispEventSimpleImpl::GetTypeInfo.md)|devuelve **E\_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfoCount](../Topic/IDispEventSimpleImpl::GetTypeInfoCount.md)|devuelve **E\_NOTIMPL**.|  
|[IDispEventSimpleImpl::Invoke](../Topic/IDispEventSimpleImpl::Invoke.md)|Llama a los controladores de eventos enumerados en el mapa de receptor de eventos.|  
|[IDispEventSimpleImpl::Unadvise](../Topic/IDispEventSimpleImpl::Unadvise.md)|Interrumpe la conexión con el origen de eventos predeterminado.|  
  
## Comentarios  
 `IDispEventSimpleImpl` proporciona una manera de implementar dispinterface de eventos sin necesidad de proporcionar el código de implementación para cada método o evento en la interfaz.  `IDispEventSimpleImpl` proporciona implementaciones de los métodos de `IDispatch` .  Solo necesita proporcionar implementaciones para los eventos que le interese administrar.  
  
 `IDispEventSimpleImpl` funciona junto con [mapa de receptor de eventos](../Topic/BEGIN_SINK_MAP.md) en la clase para distribuir eventos a la función adecuada del controlador.  para utilizar esta clase:  
  
-   Agregue una macro de [SINK\_ENTRY\_INFORMATION](../Topic/SINK_ENTRY_INFO.md) el receptor de eventos asignado para cada evento en cada objeto que desea controlar.  
  
-   Especifique la información de tipo para cada evento pasando un puntero a una estructura de [\_ATL\_FUNC\_INFORMATION](../../atl/reference/atl-func-info-structure.md) como parámetro a cada entrada.  En la plataforma x86, el valor de `_ATL_FUNC_INFO.cc` debe ser CC\_CDECL con el método de llamada de la función de devolución de llamada de \_\_stdcall.  
  
-   Llame a [DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md) para establecer la conexión entre el objeto de origen y la clase base.  
  
-   llamada [DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md) para interrumpir la conexión.  
  
 Debe derivar de `IDispEventSimpleImpl` \(con un valor único para `nID`\) para cada objeto para el que necesite controlar eventos.  Puede reutilizar esta clase base unadvising con un objeto de origen a continuación que informa de un objeto de origen diferentes, pero el número máximo de objetos de origen se pueden controlar mediante un objeto único al mismo tiempo está limitado por el número de clases base de `IDispEventSimpleImpl` .  
  
 **IDispEventSimplImpl** proporciona la misma funcionalidad que [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), a menos que no obtenga información de tipo sobre la interfaz de una biblioteca de tipos.  Los asistentes generan código basado únicamente en `IDispEventImpl`, pero puede utilizar `IDispEventSimpleImpl` agregando código a mano.  Utilice `IDispEventSimpleImpl` cuando no tiene una biblioteca de tipos que describe la interfaz de eventos ni la referencia para evitar la sobrecarga asociada al uso de la biblioteca de tipos.  
  
> [!NOTE]
>  `IDispEventImpl` y `IDispEventSimpleImpl` proporcionan su propia implementación de **IUnknown:: QueryInterface** habilitar cada clase base de `IDispEventImpl` o de `IDispEventSimpleImpl` para que actúe como identidad COM independiente mientras todavía permite acceso directo a los miembros de clase en el objeto COM principal.  
  
 La implementación de CE ATL de los receptores de eventos ActiveX solo admite valores devueltos de HRESULT tipo o void de los métodos de control de eventos; cualquier otro valor devuelto es no admitidos y su comportamiento es indefinido.  
  
 Para obtener más información, vea [admitir IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## Jerarquía de herencia  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [\_ATL\_FUNC\_INFO Structure](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl Class](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl Class](../../atl/reference/idispeventimpl-class.md)   
 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md)   
 [Class Overview](../../atl/atl-class-overview.md)