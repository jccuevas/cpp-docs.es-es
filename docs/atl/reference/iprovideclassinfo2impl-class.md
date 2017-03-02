---
title: Clase IProvideClassInfo2Impl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IProvideClassInfo2
- ATL.IProvideClassInfo2Impl
- IProvideClassInfo2Impl
- ATL::IProvideClassInfo2Impl
dev_langs:
- C++
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 0d3bed0f625e396b63ada19ded02ba9ad3b697b0
ms.lasthandoff: 02/24/2017

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
 Puntero al identificador de la coclase.  
  
 *psrcid*  
 Puntero al identificador de predeterminada de la coclase dispinterface de salida.  
  
 `plibid`  
 Puntero a LIBID de la biblioteca de tipos que contiene información acerca de la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.  
  
 `wMajor`  
 La versión principal de la biblioteca de tipos. El valor predeterminado es 1.  
  
 `wMinor`  
 La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.  
  
 `tihclass`  
 La clase utilizada para administrar la información de tipo de la coclase. El valor predeterminado es `CComTypeInfoHolder`.  
  
## <a name="members"></a>Miembros  
  
### <a name="constructors"></a>Constructores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Recupera un **ITypeInfo** puntero a información de tipo de la coclase.|  
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Recupera el GUID de la interfaz de envío del objeto salientes.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::_tih](#_tih)|Administra la información de tipo para la coclase.|  
  
## <a name="remarks"></a>Comentarios  
 El [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) interfaz extiende [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) agregando el `GetGUID` método. Este método permite que un cliente recuperar la interfaz de salida de un objeto IID para su conjunto de eventos predeterminado. Clase `IProvideClassInfo2Impl` proporciona una implementación predeterminada de la **IProvideClassInfo** y `IProvideClassInfo2` métodos.  
  
 `IProvideClassInfo2Impl`contiene un miembro estático del tipo `CComTypeInfoHolder` que administra la información de tipo de la coclase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IProvideClassInfo2`  
  
 `IProvideClassInfo2Impl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="a-namegetclassinfoa--iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a>IProvideClassInfo2Impl::GetClassInfo  
 Recupera un `ITypeInfo` puntero a información de tipo de la coclase.  
  
```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IProvideClassInfo::GetClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms690192) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetguida--iprovideclassinfo2implgetguid"></a><a name="getguid"></a>IProvideClassInfo2Impl::GetGUID  
 Recupera el GUID de la interfaz de envío del objeto salientes.  
  
```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IProvideClassInfo2::GetGUID](http://msdn.microsoft.com/library/windows/desktop/ms679721) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameiprovideclassinfo2impla--iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl  
 El constructor.  
  
```
IProvideClassInfo2Impl();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas `AddRef` en el [_tih](#_tih) miembro. El destructor llama **versión**.  
  
##  <a name="a-nametiha--iprovideclassinfo2impltih"></a><a name="_tih"></a>IProvideClassInfo2Impl::_tih  
 Este miembro de datos estático es una instancia del parámetro de plantilla de clase, `tihclass`, cuyo valor predeterminado es `CComTypeInfoHolder`.  
  
```
static  tihclass
    _tih;
```     
  
### <a name="remarks"></a>Comentarios  
 `_tih`administra la información de tipo para la coclase.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

