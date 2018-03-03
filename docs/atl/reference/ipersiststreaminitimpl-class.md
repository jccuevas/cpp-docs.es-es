---
title: Clase IPersistStreamInitImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe1bcd8d8198304c92584f01522048c4d29b827
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ipersiststreaminitimpl-class"></a>Clase IPersistStreamInitImpl
Esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfaz.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class ATL_NO_VTABLE IPersistStreamInitImpl 
   : public IPersistStreamInit
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IPersistStreamInitImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|  
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Recupera el tamaño de la secuencia necesaria para guardar los datos del objeto. Devuelve la implementación de ATL **E_NOTIMPL**.|  
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicializa un objeto recién creado.|  
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Comprueba si los datos del objeto ha cambiado desde que se guardó por última vez.|  
|[IPersistStreamInitImpl::Load](#load)|Carga las propiedades del objeto de la secuencia especificada.|  
|[IPersistStreamInitImpl::Save](#save)|Guarda las propiedades del objeto en la secuencia especificada.|  
  
## <a name="remarks"></a>Comentarios  
 El [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfaz permite que un cliente solicitar que el objeto se cargue y guarde sus datos persistentes en una sola secuencia. Clase `IPersistStreamInitImpl` proporciona una implementación predeterminada de esta interfaz e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getclassid"></a>IPersistStreamInitImpl::GetClassID  
 Recupera el CLSID del objeto.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPersist:: GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) en el SDK de Windows.  
  
##  <a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax  
 Recupera el tamaño de la secuencia necesaria para guardar los datos del objeto.  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPersistStreamInit::GetSizeMax](http://msdn.microsoft.com/library/windows/desktop/ms687287) en el SDK de Windows.  
  
##  <a name="initnew"></a>IPersistStreamInitImpl::InitNew  
 Inicializa un objeto recién creado.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234) en el SDK de Windows.  
  
##  <a name="isdirty"></a>IPersistStreamInitImpl::IsDirty  
 Comprueba si los datos del objeto ha cambiado desde que se guardó por última vez.  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPersistStreamInit::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms680092) en el SDK de Windows.  
  
##  <a name="load"></a>IPersistStreamInitImpl::Load  
 Carga las propiedades del objeto de la secuencia especificada.  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>Comentarios  
 ATL usa asignación de propiedad del objeto para recuperar esta información.  
  
 Vea [IPersistStreamInit:: Load](http://msdn.microsoft.com/library/windows/desktop/ms680730) en el SDK de Windows.  
  
##  <a name="save"></a>IPersistStreamInitImpl::Save  
 Guarda las propiedades del objeto en la secuencia especificada.  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>Comentarios  
 ATL usa asignación de propiedad del objeto para almacenar esta información.  
  
 Vea [IPersistStreamInit::Save](http://msdn.microsoft.com/library/windows/desktop/ms694439) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Almacenamientos y secuencias](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Información general de clases](../../atl/atl-class-overview.md)
