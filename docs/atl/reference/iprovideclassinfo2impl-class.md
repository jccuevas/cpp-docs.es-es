---
title: Clase IProvideClassInfo2Impl
ms.date: 11/04/2016
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
ms.openlocfilehash: 41a0756250e749a07d48ad4f090c2f1c322aa558
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276047"
---
# <a name="iprovideclassinfo2impl-class"></a>Clase IProvideClassInfo2Impl

Esta clase proporciona una implementación predeterminada de la [IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) y [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) métodos.

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

*pcoclsid*<br/>
Un puntero al identificador de la coclase.

*psrcid*<br/>
Un puntero al identificador de la predeterminada de la coclase dispinterface de salida.

*plibid*<br/>
Un puntero a LIBID de la biblioteca de tipos que contiene información acerca de la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.

*wMajor*<br/>
La versión principal de la biblioteca de tipos. El valor predeterminado es 1.

*wMinor*<br/>
La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.

*tihclass*<br/>
La clase usada para administrar la información de tipo de la coclase. El valor predeterminado es `CComTypeInfoHolder`.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|Name|Descripción|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Recupera un `ITypeInfo` puntero a la información de tipo de la coclase.|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Recupera el GUID para la dispinterface saliente del objeto.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Administra la información de tipo de la coclase.|

## <a name="remarks"></a>Comentarios

El [IProvideClassInfo2](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo2) interfaz extiende [IProvideClassInfo](/windows/desktop/api/ocidl/nn-ocidl-iprovideclassinfo) agregando el `GetGUID` método. Este método permite que un cliente recuperar la interfaz de salida de un objeto IID para su conjunto de eventos de forma predeterminada. Clase `IProvideClassInfo2Impl` proporciona una implementación predeterminada de la `IProvideClassInfo` y `IProvideClassInfo2` métodos.

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

Consulte [IProvideClassInfo::GetClassInfo](/windows/desktop/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) en el SDK de Windows.

##  <a name="getguid"></a>  IProvideClassInfo2Impl::GetGUID

Recupera el GUID para la dispinterface saliente del objeto.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Comentarios

Consulte [IProvideClassInfo2::GetGUID](/windows/desktop/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) en el SDK de Windows.

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

`_tih` Administra la información de tipo de la coclase.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
