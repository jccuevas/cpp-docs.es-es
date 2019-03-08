---
title: CInterfaceList (clase)
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: e740d891e279bb29eeef898de52698dc3f04fc67
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282466"
---
# <a name="cinterfacelist-class"></a>CInterfaceList (clase)

Esta clase proporciona métodos útiles al construir una lista de punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceList::CInterfaceList](#cinterfacelist)|El constructor de la lista de interfaces.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona un constructor y los métodos derivados para crear una lista de punteros de interfaz COM. Use [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) cuando se requiere una matriz.

Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList

El constructor de la lista de interfaces.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
El tamaño del bloque, su valor predeterminado es 10.

### <a name="remarks"></a>Comentarios

El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayor tamaño de bloque reduce las llamadas a rutinas de asignación de memoria, pero usa más recursos.

## <a name="see-also"></a>Vea también

[CAtlList (clase)](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr (clase)](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits (clase)](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
