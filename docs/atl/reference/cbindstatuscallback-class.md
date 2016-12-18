---
title: "CBindStatusCallback Class | Microsoft Docs"
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
  - "CBindStatusCallback"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asynchronous data transfer [C++]"
  - "CBindStatusCallback class"
  - "data transfer [C++]"
  - "data transfer [C++], asincrónico"
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBindStatusCallback Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa la interfaz `IBindStatusCallback`.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <class   
      T  
      , int   
      nBindFlags  
      = BINDF_ASYNCHRONOUS |   
BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>  
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx  
<T::_ThreadModel::ThreadModelNoCS>, public IBindStatusCallbackImpl<T>   
```  
  
#### Parámetros  
 `T`  
 La clase que contiene la función que se denominaría como datos se reciben.  
  
 *nBindFlags*  
 Especifica marcadores de enlace devueltos por [GetBindInfo](../Topic/CBindStatusCallback::GetBindInfo.md).  La implementación predeterminada establece el enlace para ser asincrónica, recupera la versión más reciente de datos\/objeto, y no almacena datos recuperados en la memoria caché del disco.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBindStatusCallback::CBindStatusCallback](../Topic/CBindStatusCallback::CBindStatusCallback.md)|el constructor.|  
|[CBindStatusCallback::~CBindStatusCallback](../Topic/CBindStatusCallback::~CBindStatusCallback.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBindStatusCallback::Download](../Topic/CBindStatusCallback::Download.md)|Método estático que inicia el proceso de descarga, crea un objeto de `CBindStatusCallback` , y llama a `StartAsyncDownload`.|  
|[CBindStatusCallback::GetBindInfo](../Topic/CBindStatusCallback::GetBindInfo.md)|Llamado por el moniker asincrónico para solicitar información en el tipo de enlace que se va a crear.|  
|[CBindStatusCallback::GetPriority](../Topic/CBindStatusCallback::GetPriority.md)|Llamado por el moniker asincrónico para obtener la prioridad de la operación de enlace.  la implementación de ATL devuelve `E_NOTIMPL`.|  
|[CBindStatusCallback::OnDataAvailable](../Topic/CBindStatusCallback::OnDataAvailable.md)|Denominado para proporcionar datos a la aplicación como disponible.  Lee los datos, después llama a la función pasada a él para utilizar los datos.|  
|[CBindStatusCallback::OnLowResource](../Topic/CBindStatusCallback::OnLowResource.md)|Se invoca cuando los recursos son baja.  la implementación de ATL devuelve `S_OK`.|  
|[CBindStatusCallback::OnObjectAvailable](../Topic/CBindStatusCallback::OnObjectAvailable.md)|Llamado por el moniker asincrónico para pasar un puntero de interfaz del objeto a la aplicación.  la implementación de ATL devuelve `S_OK`.|  
|[CBindStatusCallback::OnProgress](../Topic/CBindStatusCallback::OnProgress.md)|Denominado para indicar el progreso de un proceso de transferencia de datos.  la implementación de ATL devuelve `S_OK`.|  
|[CBindStatusCallback::OnStartBinding](../Topic/CBindStatusCallback::OnStartBinding.md)|Al enlazar se inicia.|  
|[CBindStatusCallback::OnStopBinding](../Topic/CBindStatusCallback::OnStopBinding.md)|Llamado cuando se detiene la transferencia de datos asincrónica.|  
|[CBindStatusCallback::StartAsyncDownload](../Topic/CBindStatusCallback::StartAsyncDownload.md)|Inicializa los bytes disponibles y los bytes leen en cero, crea un objeto de secuencia de inserción\- tipo de una dirección URL, y se llama `OnDataAvailable` cada vez que los datos están disponibles.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBindStatusCallback::m\_dwAvailableToRead](../Topic/CBindStatusCallback::m_dwAvailableToRead.md)|Número de bytes disponible para leer.|  
|[CBindStatusCallback::m\_dwTotalRead](../Topic/CBindStatusCallback::m_dwTotalRead.md)|Número total de bytes leídos.|  
|[CBindStatusCallback::m\_pFunc](../Topic/CBindStatusCallback::m_pFunc.md)|Puntero a la función llamada cuando los datos están disponibles.|  
|[CBindStatusCallback::m\_pT](../Topic/CBindStatusCallback::m_pT.md)|Puntero al objeto que solicita la transferencia de datos asincrónica.|  
|[CBindStatusCallback::m\_spBindCtx](../Topic/CBindStatusCallback::m_spBindCtx.md)|Puntero a la interfaz de [IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755) para la operación actual del enlace.|  
|[CBindStatusCallback::m\_spBinding](../Topic/CBindStatusCallback::m_spBinding.md)|Puntero a la interfaz de `IBinding` para la operación actual del enlace.|  
|[CBindStatusCallback::m\_spMoniker](../Topic/CBindStatusCallback::m_spMoniker.md)|Puntero a la interfaz de [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) para que la dirección URL utilice.|  
|[CBindStatusCallback::m\_spStream](../Topic/CBindStatusCallback::m_spStream.md)|Puntero a la interfaz de [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) para la transferencia de datos.|  
  
## Comentarios  
 La clase `CBindStatusCallback` implementa la interfaz `IBindStatusCallback`.  `IBindStatusCallback` se debe implementar a la aplicación de modo que puede recibir notificaciones de una transferencia de datos asincrónica.  El moniker asincrónico proporcionado por el sistema utiliza los métodos de `IBindStatusCallback` para enviar y recibir información sobre la descarga de datos asincrónica en el objeto.  
  
 Normalmente, el objeto de `CBindStatusCallback` está asociado a una operación específica del enlace.  Por ejemplo, en el ejemplo de [ASYNC](../../top/visual-cpp-samples.md) , cuando se establece la propiedad URL, crea un objeto de `CBindStatusCallback` en la llamada a `Download`:  
  
 [!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/CPP/cbindstatuscallback-class_1.h)]  
  
 El moniker asincrónico utiliza la función de devolución de llamada `OnData` para llamar a su aplicación cuando tiene datos.  El moniker asincrónico proporcionado por el sistema.  
  
## Jerarquía de herencia  
 `CComObjectRootBase`  
  
 `IBindStatusCallback`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `CBindStatusCallback`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)