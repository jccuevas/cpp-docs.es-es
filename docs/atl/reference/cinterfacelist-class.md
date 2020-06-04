---
title: Clase CInterfaceList
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: 0a7fd781c63e4ea084cf078e49fc9efb9cfa2d85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326787"
---
# <a name="cinterfacelist-class"></a>Clase CInterfaceList

Esta clase proporciona métodos útiles al construir una lista de punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>Parámetros

*Ⅰ*<br/>
Interfaz COM que especifica el tipo de puntero que se va a almacenar.

*piid*<br/>
Un puntero al IID de *I*.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInterfaceList::CInterfaceList](#cinterfacelist)|El constructor de la lista de interfaces.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona un constructor y métodos derivados para crear una lista de punteros de interfaz COM. Utilice [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) cuando se requiera una matriz.

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a>CInterfaceList::CInterfaceList

El constructor de la lista de interfaces.

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
El tamaño del bloque, con un valor predeterminado de 10.

### <a name="remarks"></a>Observaciones

El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Los tamaños de bloque más grandes reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.

## <a name="see-also"></a>Consulte también

[Clase CAtlList](../../atl/reference/catllist-class.md)<br/>
[Clase CComQIPtr](../../atl/reference/ccomqiptr-class.md)<br/>
[Clase CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
