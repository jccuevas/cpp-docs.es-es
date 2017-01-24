---
title: "IDispatchImpl Class | Microsoft Docs"
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
  - "IDispatchImpl"
  - "ATL.IDispatchImpl"
  - "ATL::IDispatchImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces duales, clases"
  - "IDispatch (compatibilidad de la clase en ATL)"
  - "IDispatchImpl (clase)"
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDispatchImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación predeterminada de la parte de `IDispatch` de una interfaz dual.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
template<  
   class T,  
   const IID* piid= &__uuidof(T),  
   const GUID* plibid = &CAtlModule::m_libid,  
   WORD wMajor = 1,  
   WORD wMinor = 0,  
   class tihclass = CComTypeInfoHolder   
>   
class ATL_NO_VTABLE IDispatchImpl :  
   public T  
```  
  
#### Parámetros  
 \[in\] `T`  
 una interfaz dual.  
  
 \[in\] `piid`  
 Un puntero al identificador IID de `T`.  
  
 \[in\] `plibid`  
 Un puntero al LIBID de la biblioteca de tipos que contiene información sobre la interfaz.  De forma predeterminada, se pasa la biblioteca de tipos del servidor.  
  
 \[in\] `wMajor`  
 La versión principal de la biblioteca de tipos.  de forma predeterminada, el valor es 1.  
  
 \[in\] `wMinor`  
 La versión secundaria de la biblioteca de tipos.  de forma predeterminada, el valor es 0.  
  
 \[in\] `tihclass`  
 la clase utilizada para administrar la información de tipo para `T`.  De forma predeterminada, el valor es `CComTypeInfoHolder`.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](../Topic/IDispatchImpl::IDispatchImpl.md)|el constructor.  Llama a `AddRef` en la variable miembro protegida que administra la información de tipo para la interfaz dual.  Las llamadas `Release`del destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](../Topic/IDispatchImpl::GetIDsOfNames.md)|Asigna un conjunto de nombres a un conjunto correspondiente de identificadores de envío.|  
|[IDispatchImpl::GetTypeInfo](../Topic/IDispatchImpl::GetTypeInfo.md)|Recupera información de tipo para la interfaz dual.|  
|[IDispatchImpl::GetTypeInfoCount](../Topic/IDispatchImpl::GetTypeInfoCount.md)|Determina si hay información de tipos disponible para la interfaz dual.|  
|[IDispatchImpl::Invoke](../Topic/IDispatchImpl::Invoke.md)|Proporciona acceso a las propiedades y los métodos expuestos por la interfaz dual.|  
  
## Comentarios  
 `IDispatchImpl` proporciona una implementación predeterminada de la parte de `IDispatch` de cualquier interfaz dual en un objeto.  Una interfaz dual se deriva de `IDispatch` y sólo utiliza tipos de Automatización\-compatible.  Como dispinterface, una interfaz dual admite el enlace anticipado y el enlace en tiempo de ejecución; sin embargo, una interfaz dual también admite el enlace vtable.  
  
 En el siguiente ejemplo, se muestra una implementación típica de `IDispatchImpl`.  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/CPP/idispatchimpl-class_1.h)]  
  
 De forma predeterminada, la clase de `IDispatchImpl` busca la información de tipo para `T` en el registro.  Para implementar una interfaz no registrada, puede utilizar la clase de `IDispatchImpl` sin el acceso del registro mediante un número de versión predefinido.  Si crea un objeto de `IDispatchImpl` con 0xFFFF como valor para `wMajor` y 0xFFFF como valor para `wMinor`, la clase de `IDispatchImpl` recupera la biblioteca de tipos del archivo .dll en lugar del registro.  
  
 `IDispatchImpl` contiene un miembro estático de `CComTypeInfoHolder` tipo que administran la información de tipo para la interfaz dual.  Si tiene varios objetos que implementan la misma interfaz dual, solo una instancia de `CComTypeInfoHolder` se utiliza.  
  
## Jerarquía de herencia  
 `T`  
  
 `IDispatchImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)