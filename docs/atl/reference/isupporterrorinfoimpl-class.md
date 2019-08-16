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
ms.openlocfilehash: d5e7f087f6646940777ae8b2d2a4ea888fdd3593
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495374"
---
# <a name="isupporterrorinfoimpl-class"></a>Clase ISupportErrorInfoImpl

Esta clase proporciona una implementación predeterminada de la [interfaz ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) y se puede usar cuando solo una sola interfaz genera errores en un objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

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

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Indica si la interfaz identificada `riid` por es compatible con la interfaz [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) .|

## <a name="remarks"></a>Comentarios

La [interfaz ISupportErrorInfo](/windows/win32/api/oaidl/nn-oaidl-isupporterrorinfo) garantiza que se puede devolver información de error al cliente. Los objetos que `IErrorInfo` utilizan deben `ISupportErrorInfo`implementar.

La `ISupportErrorInfoImpl` clase proporciona una implementación predeterminada `ISupportErrorInfo` de y se puede usar cuando solo una sola interfaz genera errores en un objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Indica si la interfaz identificada `riid` por es compatible con la interfaz [IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo) .

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Comentarios

Vea [ISupportErrorInfo:: InterfaceSupportsErrorInfo](/windows/win32/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
