---
title: Clase CInterfaceArray
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: e6efe31989b06f0977ecff156a8f64053dc64ad1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326799"
---
# <a name="cinterfacearray-class"></a>Clase CInterfaceArray

Esta clase proporciona métodos útiles al construir una matriz de punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|El constructor de la matriz de interfaz.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona un constructor y métodos derivados para crear una matriz de punteros de interfaz COM. Utilice [CInterfaceList](../../atl/reference/cinterfacelist-class.md) cuando se requiera una lista.

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cinterfacearraycinterfacearray"></a><a name="cinterfacearray"></a>CInterfaceArray::CInterfaceArray

El constructor.

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa la matriz de punteros inteligentes.

## <a name="see-also"></a>Consulte también

[Clase CAtlArray](../../atl/reference/catlarray-class.md)<br/>
[Clase CComQIPtr](../../atl/reference/ccomqiptr-class.md)<br/>
[Clase CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
