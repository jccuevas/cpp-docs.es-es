---
title: "IDataObjectImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDataObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "data transfer [C++]"
  - "data transfer [C++], Uniform Data Transfer"
  - "IDataObject, implementación de ATL"
  - "IDataObjectImpl class"
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDataObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para admitir la Transferencia de datos uniforme y administrar conexiones.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template< class   
      T  
      >  
class IDataObjectImpl  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IDataObjectImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDataObjectImpl::DAdvise](../Topic/IDataObjectImpl::DAdvise.md)|Establece una conexión entre el objeto de datos y un receptor advise.  Esto permite al receptor advise para recibir notificaciones de cambios en el objeto.|  
|[IDataObjectImpl::DUnadvise](../Topic/IDataObjectImpl::DUnadvise.md)|finaliza una conexión establecida previamente con `DAdvise`.|  
|[IDataObjectImpl::EnumDAdvise](../Topic/IDataObjectImpl::EnumDAdvise.md)|Crea un enumerador para recorrer en iteración las conexiones de consulta actuales.|  
|[IDataObjectImpl::EnumFormatEtc](../Topic/IDataObjectImpl::EnumFormatEtc.md)|Crea un enumerador para recorrer en iteración las estructuras de **FORMATETC** admitidas por el objeto de datos.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IDataObjectImpl::FireDataChange](../Topic/IDataObjectImpl::FireDataChange.md)|Envía una notificación a cada indican el receptor.|  
|[IDataObjectImpl::GetCanonicalFormatEtc](../Topic/IDataObjectImpl::GetCanonicalFormatEtc.md)|Recupera una estructura equivalente de **FORMATETC** a una que es más complejo.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IDataObjectImpl::GetData](../Topic/IDataObjectImpl::GetData.md)|Transfiere datos del objeto de datos al cliente.  Los datos se describe en una estructura de **FORMATETC** y se transfiere a través de una estructura de **STGMEDIUM** .|  
|[IDataObjectImpl::GetDataHere](../Topic/IDataObjectImpl::GetDataHere.md)|Similar a `GetData`, a menos que el cliente debe asignar la estructura de **STGMEDIUM** .  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IDataObjectImpl::QueryGetData](../Topic/IDataObjectImpl::QueryGetData.md)|determina si el objeto de datos admite una estructura determinada de **FORMATETC** para transferir datos.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IDataObjectImpl::SetData](../Topic/IDataObjectImpl::SetData.md)|Transfiere datos del cliente al objeto de datos.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
  
## Comentarios  
 La interfaz de [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) proporciona métodos que permiten la Transferencia de datos uniforme admiten.  `IDataObject` usa estructuras [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) y [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) de formato estándar para recuperar y almacenar datos.  
  
 `IDataObject` también administra conexiones para advertir a los receptores para el consumidor de los datos.  Para que el cliente reciba notificaciones de los datos del objeto de datos, el cliente debe implementar la interfaz de [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) en un objeto denominado receptor advise.  Cuando el cliente llama **IDataObject:: DAdvise**, una conexión se establece entre el objeto de datos y el receptor advise.  
  
 La clase `IDataObjectImpl` proporciona una implementación predeterminada de `IDataObject` e implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)