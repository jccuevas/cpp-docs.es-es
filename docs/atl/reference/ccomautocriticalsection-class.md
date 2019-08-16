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
ms.openlocfilehash: 116c550f45bf622e7620b3a6f552339b4bcc24a7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497933"
---
# <a name="ccomautocriticalsection-class"></a>Clase CComAutoCriticalSection

`CComAutoCriticalSection`proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.

## <a name="syntax"></a>Sintaxis

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|El constructor.|
|[CComAutoCriticalSection::~CComAutoCriticalSection](#dtor)|Destructor.|

## <a name="remarks"></a>Comentarios

`CComAutoCriticalSection`es similar a la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), `CComAutoCriticalSection` excepto que inicializa automáticamente el objeto de sección crítica en el constructor.

Normalmente, se usa `CComAutoCriticalSection` a través `typedef` del nombre [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Este nombre hace `CComAutoCriticalSection` referencia al uso de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .

Los `Init` métodos `Term` y de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) no están disponibles cuando se usa esta clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore. h

##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection

El constructor.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Comentarios

Llama a la función [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)de Win32, que inicializa el objeto de sección crítica.

##  <a name="dtor"></a>  CComAutoCriticalSection::~CComAutoCriticalSection

Destructor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Comentarios

El destructor llama a [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), que libera todos los recursos del sistema utilizados por el objeto de sección crítica.

## <a name="see-also"></a>Vea también

[CComFakeCriticalSection (clase)](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection (clase)](../../atl/reference/ccomcriticalsection-class.md)
