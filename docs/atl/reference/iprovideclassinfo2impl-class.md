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
ms.openlocfilehash: f0ff3607002d32b4e21f7fc2199cc5da3662af8b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495537"
---
# <a name="iprovideclassinfo2impl-class"></a>Clase IProvideClassInfo2Impl

Esta clase proporciona una implementación predeterminada de los métodos [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) y [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) .

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
Puntero al identificador de la coclase.

*psrcid*<br/>
Puntero al identificador de la interfaz dispinterface de salida predeterminada de la coclase.

*plibid*<br/>
Puntero al LIBId de la biblioteca de tipos que contiene información sobre la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.

*wMajor*<br/>
La versión principal de la biblioteca de tipos. El valor predeterminado es 1.

*wMinor*<br/>
La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.

*tihclass*<br/>
Clase usada para administrar la información de tipo de la coclase. El valor predeterminado es `CComTypeInfoHolder`.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Recupera un `ITypeInfo` puntero a la información de tipo de la coclase.|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Recupera el GUID para la dispinterface de salida del objeto.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Administra la información de tipo para la coclase.|

## <a name="remarks"></a>Comentarios

La interfaz [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) extiende [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) agregando el `GetGUID` método. Este método permite a un cliente recuperar el IID de la interfaz de salida de un objeto para su conjunto de eventos predeterminado. La `IProvideClassInfo2Impl` clase proporciona una implementación predeterminada de `IProvideClassInfo` los `IProvideClassInfo2` métodos y.

`IProvideClassInfo2Impl`contiene un miembro estático de tipo `CComTypeInfoHolder` que administra la información de tipo para la coclase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="getclassinfo"></a>  IProvideClassInfo2Impl::GetClassInfo

Recupera un `ITypeInfo` puntero a la información de tipo de la coclase.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Comentarios

Vea [IProvideClassInfo:: GetClassInfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) en el Windows SDK.

##  <a name="getguid"></a>  IProvideClassInfo2Impl::GetGUID

Recupera el GUID para la dispinterface de salida del objeto.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Comentarios

Vea [IProvideClassInfo2:: GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) en el Windows SDK.

##  <a name="iprovideclassinfo2impl"></a>  IProvideClassInfo2Impl::IProvideClassInfo2Impl

El constructor.

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Comentarios

Llama `AddRef` a en el miembro [_tih](#_tih) . El destructor llama a `Release`.

##  <a name="_tih"></a>  IProvideClassInfo2Impl::_tih

Este miembro de datos estático es una instancia del parámetro de plantilla de clase, *tihclass*, que de `CComTypeInfoHolder`forma predeterminada es.

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Comentarios

`_tih`administra la información de tipo para la coclase.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
