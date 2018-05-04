---
title: Clase IPersistStorageImpl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
dev_langs:
- C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18f03ba235fdfc14dba22f1759240bd5fb72bafd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ipersiststorageimpl-class"></a>Clase IPersistStorageImpl
Esta clase implementa la [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) interfaz.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IPersistStorageImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPersistStorageImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|  
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Indica al objeto para liberar todos los objetos de almacenamiento y entrar en el modo de HandsOff. Devuelve la implementación de ATL `S_OK`.|  
|[IPersistStorageImpl::InitNew](#initnew)|Inicializa un nuevo almacenamiento.|  
|[IPersistStorageImpl::IsDirty](#isdirty)|Comprueba si los datos del objeto ha cambiado desde que se guardó por última vez.|  
|[IPersistStorageImpl::Load](#load)|Carga las propiedades del objeto desde el almacenamiento especificado.|  
|[IPersistStorageImpl::Save](#save)|Guarda las propiedades del objeto en el almacenamiento especificado.|  
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Notifica a un objeto que puede volver al modo Normal para escribir en su objeto de almacenamiento. Devuelve la implementación de ATL `S_OK`.|  
  
## <a name="remarks"></a>Comentarios  
 `IPersistStorageImpl` implementa el [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) interfaz, lo que permite a un cliente para solicitar que la carga del objeto y guardar sus datos persistentes con un almacenamiento de información.  
  
 La implementación de esta clase requiere la clase `T` para realizar una implementación de la `IPersistStreamInit` disponibles a través de la interfaz `QueryInterface`. Normalmente, esto significa esa clase `T` debe derivarse de [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), proporcionar una entrada para `IPersistStreamInit` en el [mapa COM](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)y usar un [deasignacióndepropiedad](http://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427) para describir los datos persistentes de la clase.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID  
 Recupera el CLSID del objeto.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPersist:: GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) en el SDK de Windows.  
  
##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage  
 Indica al objeto para liberar todos los objetos de almacenamiento y entrar en el modo de HandsOff.  
  
```
STDMETHOD(HandsOffStorage)(void);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/windows/desktop/ms679742) en el SDK de Windows.  
  
##  <a name="initnew"></a>  IPersistStorageImpl::InitNew  
 Inicializa un nuevo almacenamiento.  
  
```
STDMETHOD(InitNew)(IStorage*);
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación de ATL se delega a la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfaz.  
  
 Vea [IPersistStorage:InitNew](http://msdn.microsoft.com/library/windows/desktop/ms687194) en el SDK de Windows.  
  
##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty  
 Comprueba si los datos del objeto ha cambiado desde que se guardó por última vez.  
  
```
STDMETHOD(IsDirty)(void);
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación de ATL se delega a la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfaz.  
  
 Vea [IPersistStorage:IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910) en el SDK de Windows.  
  
##  <a name="load"></a>  IPersistStorageImpl::Load  
 Carga las propiedades del objeto desde el almacenamiento especificado.  
  
```
STDMETHOD(Load)(IStorage* pStorage);
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación de ATL se delega a la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfaz. **Carga** usa una secuencia denominada "Contenido" para recuperar los datos del objeto. El [guardar](#save) método originalmente crea esta secuencia.  
  
 Vea [IPersistStorage:Load](http://msdn.microsoft.com/library/windows/desktop/ms680557) en el SDK de Windows.  
  
##  <a name="save"></a>  IPersistStorageImpl::Save  
 Guarda las propiedades del objeto en el almacenamiento especificado.  
  
```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación de ATL se delega a la [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) interfaz. Cuando **guardar** primero llama, crea una secuencia denominada "Contenido" en el almacenamiento especificado. Este flujo, a continuación, se utiliza en llamadas posteriores a **guardar** y en las llamadas a [carga](#load).  
  
 Vea [IPersistStorage:Save](http://msdn.microsoft.com/library/windows/desktop/ms680680) en el SDK de Windows.  
  
##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted  
 Notifica a un objeto que puede volver al modo Normal para escribir en su objeto de almacenamiento.  
  
```
STDMETHOD(SaveCompleted)(IStorage*);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [IPersistStorage:SaveCompleted](http://msdn.microsoft.com/library/windows/desktop/ms679713) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Almacenamientos y secuencias](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Clase IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [Clase IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
