---
title: "IProvideClassInfo2Impl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IProvideClassInfo2"
  - "ATL.IProvideClassInfo2Impl"
  - "IProvideClassInfo2Impl"
  - "ATL::IProvideClassInfo2Impl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "class information, ATL"
  - "IProvideClassInfo2 ATL implementation"
  - "IProvideClassInfo2Impl class"
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IProvideClassInfo2Impl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase proporciona una implementación predeterminada de los métodos de [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) y de [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) .  
  
## Sintaxis  
  
```  
  
      template <  
   const CLSID* pcoclsid,  
   const IID* psrcid,  
   const GUID* plibid = &CAtlModule::m_libid,  
   WORD wMajor = 1,  
   WORD wMinor = 0,  
   class tihclass = CComTypeInfoHolder   
>  
class ATL_NO_VTABLE IProvideClassInfo2Impl :  
   public IProvideClassInfo2  
```  
  
#### Parámetros  
 *pcoclsid*  
 Un puntero al identificador de la coclase.  
  
 *psrcid*  
 Un puntero al identificador del dispinterface saliente predeterminado coclass.  
  
 `plibid`  
 Un puntero al LIBID de la biblioteca de tipos que contiene información sobre la interfaz.  De forma predeterminada, se pasa la biblioteca de tipos del servidor.  
  
 `wMajor`  
 La versión principal de la biblioteca de tipos.  El valor predeterminado es 1.  
  
 `wMinor`  
 La versión secundaria de la biblioteca de tipos.  El valor predeterminado es 0.  
  
 `tihclass`  
 La clase utilizada para administrar la información de tipo coclass.  El valor predeterminado es `CComTypeInfoHolder`.  
  
## Members  
  
### Constructores  
  
|Name|Descripción|  
|----------|-----------------|  
|[IProvideClassInfo2Impl:: IProvideClassInfo2Impl](../Topic/IProvideClassInfo2Impl::IProvideClassInfo2Impl.md)|Constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::GetClassInfo](../Topic/IProvideClassInfo2Impl::GetClassInfo.md)|Recupera un puntero de **ITypeInfo** a la información de tipo coclass.|  
|[IProvideClassInfo2Impl::GetGUID](../Topic/IProvideClassInfo2Impl::GetGUID.md)|Recupera el GUID para el dispinterface saliente del objeto.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::\_tih](../Topic/IProvideClassInfo2Impl::_tih.md)|Administra la información de tipo de la coclase.|  
  
## Comentarios  
 la interfaz de [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) extiende [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) agregando el método de `GetGUID` .  Este método permite que un cliente recupere la interfaz de salida IID de un objeto para el conjunto de eventos predeterminado.  la clase `IProvideClassInfo2Impl` proporciona una implementación predeterminada de los métodos de **IProvideClassInfo** y de `IProvideClassInfo2` .  
  
 `IProvideClassInfo2Impl` contiene un miembro estático de `CComTypeInfoHolder` tipo que administran la información de tipo de la coclase.  
  
## Jerarquía de herencia  
 `IProvideClassInfo2`  
  
 `IProvideClassInfo2Impl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)