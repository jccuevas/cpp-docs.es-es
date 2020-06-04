---
title: Clase ISupportErrorInfoImpl
ms.date: 06/13/2019
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: 4c60b58ba697f00b146077a2cdecd727fe2cac02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326367"
---
# <a name="isupporterrorinfoimpl-class"></a>Clase ISupportErrorInfoImpl

Esta clase proporciona una implementación predeterminada de la [interfaz ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) y se puede utilizar cuando solo una interfaz genera errores en un objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>Parámetros

*piid*<br/>
Puntero al IID de una interfaz que admite [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Indica si la interfaz identificada por `riid` admite la interfaz [IErrorInfo.](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)|

## <a name="remarks"></a>Observaciones

La [interfaz ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) garantiza que la información de error se puede devolver al cliente. Los objetos que usan `IErrorInfo` deben implementarse `ISupportErrorInfo`.

Clase `ISupportErrorInfoImpl` proporciona una `ISupportErrorInfo` implementación predeterminada de y se puede utilizar cuando solo una interfaz genera errores en un objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="isupporterrorinfoimplinterfacesupportserrorinfo"></a><a name="interfacesupportserrorinfo"></a>ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Indica si la interfaz identificada por `riid` admite la interfaz [IErrorInfo.](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Observaciones

Consulte [ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
