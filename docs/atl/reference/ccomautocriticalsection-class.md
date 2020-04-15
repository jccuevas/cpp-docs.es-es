---
title: Clase CComAutoCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 8cbf08082fd24ef2cf0e8794e2944a799baec084
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321088"
---
# <a name="ccomautocriticalsection-class"></a>Clase CComAutoCriticalSection

`CComAutoCriticalSection`proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítico.

## <a name="syntax"></a>Sintaxis

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|El constructor.|
|[CComAutoCriticalSection::-CComAutoCriticalSection](#dtor)|Destructor.|

## <a name="remarks"></a>Observaciones

`CComAutoCriticalSection`es similar a la clase `CComAutoCriticalSection` [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), excepto que inicializa automáticamente el objeto de sección crítica en el constructor.

Normalmente, se `CComAutoCriticalSection` usa `typedef` a través del nombre [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Este nombre `CComAutoCriticalSection` hace referencia cuando se usa [CComMultiThreadModel.](../../atl/reference/ccommultithreadmodel-class.md)

Los `Init` `Term` métodos y de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) no están disponibles cuando se utiliza esta clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="ccomautocriticalsection"></a>CComAutoCriticalSection::CComAutoCriticalSection

El constructor.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Observaciones

Llama a la función [Win32 InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), que inicializa el objeto de sección crítica.

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="dtor"></a>CComAutoCriticalSection::-CComAutoCriticalSection

Destructor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Observaciones

El destructor llama a [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), que libera todos los recursos del sistema utilizados por el objeto de sección crítica.

## <a name="see-also"></a>Consulte también

[Clase CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)
