---
title: Clase IProvideClassInfo2Impl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
dev_langs:
- C++
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7e0bd440e2e4bd8d32525fe4be6aaad2c401f6a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880627"
---
# <a name="iprovideclassinfo2impl-class"></a>Clase IProvideClassInfo2Impl
Esta clase proporciona una implementación predeterminada de la [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) y [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) métodos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>  
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```  
  
#### <a name="parameters"></a>Parámetros  
 *pcoclsid*  
 Un puntero al identificador de la coclase.  
  
 *psrcid*  
 Un puntero al identificador de la predeterminada de la coclase dispinterface de salida.  
  
 *plibid*  
 Un puntero a LIBID de la biblioteca de tipos que contiene información acerca de la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.  
  
 *wMajor*  
 La versión principal de la biblioteca de tipos. El valor predeterminado es 1.  
  
 *wMinor*  
 La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.  
  
 *tihclass*  
 La clase usada para administrar la información de tipo de la coclase. El valor predeterminado es `CComTypeInfoHolder`.  
  
## <a name="members"></a>Miembros  
  
### <a name="constructors"></a>Constructores  
  
|nombre|Descripción|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Recupera un `ITypeInfo` puntero a la información de tipo de la coclase.|  
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Recupera el GUID para la dispinterface saliente del objeto.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::_tih](#_tih)|Administra la información de tipo de la coclase.|  
  
## <a name="remarks"></a>Comentarios  
 El [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) interfaz extiende [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) agregando el `GetGUID` método. Este método permite que un cliente recuperar la interfaz de salida de un objeto IID para su conjunto de eventos de forma predeterminada. Clase `IProvideClassInfo2Impl` proporciona una implementación predeterminada de la `IProvideClassInfo` y `IProvideClassInfo2` métodos.  
  
 `IProvideClassInfo2Impl` contiene un miembro estático del tipo `CComTypeInfoHolder` que administra la información de tipo de la coclase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IProvideClassInfo2`  
  
 `IProvideClassInfo2Impl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="getclassinfo"></a>  IProvideClassInfo2Impl::GetClassInfo  
 Recupera un `ITypeInfo` puntero a la información de tipo de la coclase.  
  
```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IProvideClassInfo::GetClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms690192) en el SDK de Windows.  
  
##  <a name="getguid"></a>  IProvideClassInfo2Impl::GetGUID  
 Recupera el GUID para la dispinterface saliente del objeto.  
  
```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IProvideClassInfo2::GetGUID](http://msdn.microsoft.com/library/windows/desktop/ms679721) en el SDK de Windows.  
  
##  <a name="iprovideclassinfo2impl"></a>  IProvideClassInfo2Impl::IProvideClassInfo2Impl  
 El constructor.  
  
```
IProvideClassInfo2Impl();
```  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas `AddRef` en el [_tih](#_tih) miembro. El destructor llama a `Release`.  
  
##  <a name="_tih"></a>  IProvideClassInfo2Impl::_tih  
 Este miembro de datos estático es una instancia del parámetro de plantilla de clase, *tihclass*, cuyo valor predeterminado es `CComTypeInfoHolder`.  
  
```
static  tihclass
    _tih;
```     
  
### <a name="remarks"></a>Comentarios  
 `_tih` administra la información de tipo de la coclase.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
