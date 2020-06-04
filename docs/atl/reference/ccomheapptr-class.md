---
title: Clase CComHeapPtr
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: 78cadfff9a278cf080393ab919f3891b201c91aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327778"
---
# <a name="ccomheapptr-class"></a>Clase CComHeapPtr

Una clase de puntero inteligente para administrar punteros de montón.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto que se va a almacenar en el montón.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComheapPtr::CComheapPtr](#ccomheapptr)|El constructor.|

## <a name="remarks"></a>Observaciones

`CComHeapPtr`deriva de `CHeapPtr`, pero usa [CComAllocator](../../atl/reference/ccomallocator-class.md) para asignar memoria mediante rutinas COM. Consulte [CHeapPtr](../../atl/reference/cheapptr-class.md) y [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) para obtener los métodos disponibles.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a>CComheapPtr::CComheapPtr

El constructor.

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
Objeto `CComHeapPtr` existente.

### <a name="remarks"></a>Observaciones

El puntero de montón se `CComHeapPtr` puede crear opcionalmente utilizando un objeto existente. Si es así, el nuevo `CComHeapPtr` objeto asume la responsabilidad de administrar el nuevo puntero y los recursos.

## <a name="see-also"></a>Consulte también

[Clase CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Clase CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Clase CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
