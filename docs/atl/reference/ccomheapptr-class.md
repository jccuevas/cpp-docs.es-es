---
title: CComHeapPtr (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3455e88c5a9852c902702544a0f915e8d20dc64e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043240"
---
# <a name="ccomheapptr-class"></a>CComHeapPtr (clase)

Una clase de puntero inteligente para administrar los punteros de montón.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto que se almacenará en el montón.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|El constructor.|

## <a name="remarks"></a>Comentarios

`CComHeapPtr` se deriva de `CHeapPtr`, pero usa [CComAllocator](../../atl/reference/ccomallocator-class.md) para asignar memoria usa COM rutinas. Consulte [CHeapPtr](../../atl/reference/cheapptr-class.md) y [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) para los métodos disponibles.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="ccomheapptr"></a>  CComHeapPtr::CComHeapPtr

El constructor.

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
Objeto `CComHeapPtr` existente.

### <a name="remarks"></a>Comentarios

El puntero del montón, opcionalmente, puede crearse una existente `CComHeapPtr` objeto. Si es así, el nuevo `CComHeapPtr` objeto asume la responsabilidad de administrar los recursos y el nuevo puntero.

## <a name="see-also"></a>Vea también

[CHeapPtr (clase)](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase (clase)](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator (clase)](../../atl/reference/ccomallocator-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
