---
title: ISupportErrorInfoImpl (clase)
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
ms.openlocfilehash: 650d90c9ec98754e11586f63e0871b70ebbe34f3
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141704"
---
# <a name="isupporterrorinfoimpl-class"></a>ISupportErrorInfoImpl (clase)

Esta clase proporciona una implementación predeterminada de la [interfaz ISupportErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) y puede usarse cuando solo una sola interfaz genera errores en un objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```cpp
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

### <a name="parameters"></a>Parámetros

*piid*<br/>
Un puntero para el IID de interfaz que admite [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Indica si la interfaz identificada por `riid` admite el [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interfaz.|

## <a name="remarks"></a>Comentarios

El [interfaz ISupportErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) garantiza que la información de error se puede devolver al cliente. Los objetos que utilizan `IErrorInfo` debe implementar `ISupportErrorInfo`.

Clase `ISupportErrorInfoImpl` proporciona una implementación predeterminada de `ISupportErrorInfo` y puede usarse cuando solo una sola interfaz genera errores en un objeto. Por ejemplo:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Indica si la interfaz identificada por `riid` admite el [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) interfaz.

```cpp
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Comentarios

Consulte [ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
