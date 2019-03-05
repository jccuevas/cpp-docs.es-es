---
title: CInterfaceArray (clase)
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: 2e8714bf40e99a1014d7cd6de82cddb13cbbb9cf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282830"
---
# <a name="cinterfacearray-class"></a>CInterfaceArray (clase)

Esta clase proporciona métodos útiles al construir una matriz de punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parámetros

*I*<br/>
Una interfaz COM que especifica el tipo de puntero que se almacenará.

*piid*<br/>
Un puntero para el IID de *me*.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|El constructor de la matriz de interfaz.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona un constructor y los métodos derivados para crear una matriz de punteros de interfaz COM. Use [CInterfaceList](../../atl/reference/cinterfacelist-class.md) cuando se necesita una lista.

Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray

El constructor.

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Comentarios

Inicializa la matriz de puntero inteligente.

## <a name="see-also"></a>Vea también

[CAtlArray (clase)](../../atl/reference/catlarray-class.md)<br/>
[CComQIPtr (clase)](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits (clase)](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
