---
title: "IDispEventImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDispEventImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventImpl class"
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# IDispEventImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona implementaciones de los métodos de `IDispatch` .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template <  
UINT nID,  
class T,  
const IID* pdiid= &IID_NULL,  
const GUID* plibid= &GUID_NULL,  
WORD wMajor= 0,  
WORD wMinor= 0,  
class tihclass= CcomTypeInfoHolder  
>  
class ATL_NO_VTABLE IDispEventImpl :  
public IDispEventSimpleImpl<nID, T, pdiid>  
```  
  
#### Parámetros  
 `nID`  
 un identificador único para el objeto de origen.  Cuando `IDispEventImpl` es la clase base para un control compuesto, utilice el Id. de recurso de control contenido deseado para este parámetro.  en otros casos, utilice un entero positivo arbitrario.  
  
 `T`  
 La clase de usuario, que es derivada de `IDispEventImpl`.  
  
 `pdiid`  
 El puntero al identificador IID dispinterface de evento implementado por esta clase.  Esta interfaz se debe definir en la biblioteca de tipos indicado por `plibid`, `wMajor`, y `wMinor`.  
  
 `plibid`  
 Un puntero a la biblioteca de tipos que define la interfaz de envío al que `pdiid`.  Si **el &GUID\_NULL**, la biblioteca de tipos es carga de compra de componentes de objeto los eventos.  
  
 `wMajor`  
 La versión principal de la biblioteca de tipos.  El valor predeterminado es 0.  
  
 `wMinor`  
 La versión secundaria de la biblioteca de tipos.  El valor predeterminado es 0.  
  
 `tihclass`  
 la clase utilizada para administrar la información de tipo para `T`.  el valor predeterminado es una clase de `CComTypeInfoHolder`escrito; sin embargo, puede reemplazar este parámetro de plantilla proporciona una clase de un tipo distinto de `CComTypeInfoHolder`.  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispEventImpl::\_tihclass](../../atl/reference/idispeventimpl-class.md)|la clase utilizada para administrar la información de tipo.  De manera predeterminada, es `CComTypeInfoHolder`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispEventImpl::IDispEventImpl](../Topic/IDispEventImpl::IDispEventImpl.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispEventImpl::GetFuncInfoFromId](../Topic/IDispEventImpl::GetFuncInfoFromId.md)|establece el índice de la función para el identificador de envío especificado.|  
|[IDispEventImpl::GetIDsOfNames](../Topic/IDispEventImpl::GetIDsOfNames.md)|Asigna un único miembro y un conjunto opcional de nombres de argumentos a un conjunto correspondiente de identificadores dispid entero.|  
|[IDispEventImpl::GetTypeInfo](../Topic/IDispEventImpl::GetTypeInfo.md)|Recupera información de tipo para un objeto.|  
|[IDispEventImpl::GetTypeInfoCount](../Topic/IDispEventImpl::GetTypeInfoCount.md)|recupera el número de interfaces de la información de tipo.|  
|[IDispEventImpl::GetUserDefinedType](../Topic/IDispEventImpl::GetUserDefinedType.md)|recupera el tipo básico de un tipo definido por el usuario.|  
  
## Comentarios  
 `IDispEventImpl` proporciona una manera de implementar dispinterface de eventos sin necesidad de proporcionar el código de implementación para cada método o evento en la interfaz.  `IDispEventImpl` proporciona implementaciones de los métodos de `IDispatch` .  Solo necesita proporcionar implementaciones para los eventos que le interese administrar.  
  
 `IDispEventImpl` funciona junto con [mapa de receptor de eventos](../Topic/BEGIN_SINK_MAP.md) en la clase para distribuir eventos a la función adecuada del controlador.  para utilizar esta clase:  
  
 Agregue [SINK\_ENTRY](../Topic/SINK_ENTRY.md) o la macro de [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY_EX.md) el receptor de eventos asigna para cada evento en cada objeto que desea controlar.  Al utilizar `IDispEventImpl` como clase base de un control compuesto, puede llamar a [AtlAdviseSinkMap](../Topic/AtlAdviseSinkMap.md) para establecer y para interrumpir la conexión con los orígenes de eventos para todas las entradas en el mapa del receptor de eventos.  En otros casos, o para el mayor control, llamada [DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md) para establecer la conexión entre el objeto de origen y la clase base.  llamada [DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md) para interrumpir la conexión.  
  
 Debe derivar de `IDispEventImpl` \(con un valor único para `nID`\) para cada objeto para el que necesite controlar eventos.  Puede reutilizar esta clase base unadvising con un objeto de origen a continuación que informa de un objeto de origen diferentes, pero el número máximo de objetos de origen se pueden controlar mediante un objeto único al mismo tiempo está limitado por el número de clases base de `IDispEventImpl` .  
  
 `IDispEventImpl` proporciona la misma funcionalidad que [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), a menos que obtiene información de tipo sobre la interfaz de una biblioteca de tipos en lugar de teniéndola proporcionado como puntero a una estructura de [\_ATL\_FUNC\_INFORMATION](../../atl/reference/atl-func-info-structure.md) .  Utilice `IDispEventSimpleImpl` cuando no tiene una biblioteca de tipos que describe la interfaz de eventos ni la referencia para evitar la sobrecarga asociada al uso de la biblioteca de tipos.  
  
> [!NOTE]
>  `IDispEventImpl` y `IDispEventSimpleImpl` proporcionan su propia implementación de **IUnknown:: QueryInterface** habilitar cada clase base de `IDispEventImpl` y de `IDispEventSimpleImpl` para que actúe como identidad COM independiente mientras todavía permite acceso directo a los miembros de clase en el objeto COM principal.  
  
 La implementación de CE ATL de los receptores de eventos ActiveX solo admite valores devueltos de HRESULT tipo o void de los métodos de control de eventos; cualquier otro valor devuelto es no admitidos y su comportamiento es indefinido.  
  
 Para obtener más información, vea [admitir IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## Jerarquía de herencia  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [\_ATL\_FUNC\_INFO Structure](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl Class](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl Class](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK\_ENTRY](../Topic/SINK_ENTRY.md)   
 [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY_EX.md)   
 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md)   
 [Class Overview](../../atl/atl-class-overview.md)