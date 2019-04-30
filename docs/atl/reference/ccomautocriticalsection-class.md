---
title: CComAutoCriticalSection (clase)
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 613440eceb71f0277f4cc5de2af89fe263772797
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260199"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection (clase)

`CComAutoCriticalSection` Proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|El constructor.|
|[CComAutoCriticalSection::~CComAutoCriticalSection](#dtor)|Destructor.|

## <a name="remarks"></a>Comentarios

`CComAutoCriticalSection` es similar a la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), excepto `CComAutoCriticalSection` automáticamente inicializa el objeto de sección crítica en el constructor.

Normalmente, se utiliza `CComAutoCriticalSection` a través de la `typedef` nombre [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Este nombre hace referencia a `CComAutoCriticalSection` cuando [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) se está usando.

El `Init` y `Term` métodos desde [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) no están disponibles cuando se usa esta clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection

El constructor.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Comentarios

Llama a la función de Win32 [InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection), que inicializa el objeto de sección crítica.

##  <a name="dtor"></a>  CComAutoCriticalSection::~CComAutoCriticalSection

Destructor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Comentarios

El destructor llama a [DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection), que libera todos los recursos del sistema utilizados por el objeto de sección crítica.

## <a name="see-also"></a>Vea también

[CComFakeCriticalSection (clase)](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md)
