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
ms.openlocfilehash: 0d1ee9acc1cfabc71ecf33fcb5919d826899c671
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329571"
---
# <a name="iprovideclassinfo2impl-class"></a>Clase IProvideClassInfo2Impl

Esta clase proporciona una implementación predeterminada de la [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) y [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) métodos.

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
Puntero al identificador de la interfaz dispinterface saliente predeterminada de la coclase.

*plibid*<br/>
Puntero al LIBID de la biblioteca de tipos que contiene información sobre la interfaz. De forma predeterminada, se pasa la biblioteca de tipos de nivel de servidor.

*wMajor*<br/>
La versión principal de la biblioteca de tipos. El valor predeterminado es 1.

*wMinor*<br/>
La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.

*tihclass*<br/>
La clase utilizada para administrar la información de tipo de la coclase. El valor predeterminado es `CComTypeInfoHolder`.

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|Nombre|Descripción|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Recupera un `ITypeInfo` puntero a la información de tipo de la coclase.|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Recupera el GUID de la interfaz dispinterface saliente del objeto.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|Administra la información de tipo para la coclase.|

## <a name="remarks"></a>Observaciones

El [IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2) interfaz extiende [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) agregando el `GetGUID` método. Este método permite a un cliente recuperar el IID de interfaz saliente de un objeto para su conjunto de eventos predeterminado. Clase `IProvideClassInfo2Impl` proporciona una implementación predeterminada de los `IProvideClassInfo` métodos y. `IProvideClassInfo2`

`IProvideClassInfo2Impl`contiene un miembro `CComTypeInfoHolder` estático de tipo que administra la información de tipo para la coclase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a>IProvideClassInfo2Impl::GetClassInfo

Recupera un `ITypeInfo` puntero a la información de tipo de la coclase.

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Observaciones

Vea [IProvideClassInfo::GetClassInfo](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) en el Windows SDK.

## <a name="iprovideclassinfo2implgetguid"></a><a name="getguid"></a>IProvideClassInfo2Impl::GetGUID

Recupera el GUID de la interfaz dispinterface saliente del objeto.

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>Observaciones

Consulte [IProvideClassInfo2::GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) en el Windows SDK.

## <a name="iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl

El constructor.

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>Observaciones

Llama `AddRef` al miembro [de _tih.](#_tih) El destructor llama a `Release`.

## <a name="iprovideclassinfo2impl_tih"></a><a name="_tih"></a>IProvideClassInfo2Impl::_tih

Este miembro de datos estáticos es una instancia del parámetro `CComTypeInfoHolder`de plantilla de clase, *tihclass*, que de forma predeterminada es .

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>Observaciones

`_tih`administra la información de tipo para la coclase.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
