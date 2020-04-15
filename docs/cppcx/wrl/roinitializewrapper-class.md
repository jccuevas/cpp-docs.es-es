---
title: RoInitializeWrapper (Clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
ms.openlocfilehash: eba9162f17b98d13a9caf956b4f110b89dd81c37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371227"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper (Clase)

Inicializa Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Observaciones

`RoInitializeWrapper`es una comodidad que inicializa Windows Runtime y devuelve un HRESULT que indica si la operación se realizó correctamente. Dado que el `::Windows::Foundation::Uninitialize`destructor de `RoInitializeWrapper` clase llama a , las instancias de deben declararse en el ámbito global o de nivel superior.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                                    | Descripción
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | Inicializa una nueva instancia de la clase `RoInitializeWrapper`.
[RoInitializeWrapper::-RoInitializeWrapper](#tilde-roinitializewrapper) | Destruye la instancia actual `RoInitializeWrapper` de la clase.

### <a name="public-operators"></a>Operadores públicos

Nombre                                       | Descripción
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | Recupera el HRESULT generado `RoInitializeWrapper` por el constructor.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RoInitializeWrapper`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers

## <a name="roinitializewrapperhresult"></a><a name="hresult"></a>RoInitializeWrapper::HRESULT()

Recupera el valor HRESULT generado `RoInitializeWrapper` por el último constructor.

```cpp
operator HRESULT()
```

## <a name="roinitializewrapperroinitializewrapper"></a><a name="roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

Inicializa una nueva instancia de la clase `RoInitializeWrapper`.

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>Parámetros

*Banderas*<br/>
Una de las enumeraciones RO_INIT_TYPE, que especifica la compatibilidad proporcionada por Windows Runtime.

### <a name="remarks"></a>Observaciones

La `RoInitializeWrapper` clase `Windows::Foundation::Initialize(flags)`invoca .

## <a name="roinitializewrapperroinitializewrapper"></a><a name="tilde-roinitializewrapper"></a>RoInitializeWrapper::-RoInitializeWrapper

Uninitializes el tiempo de ejecución de Windows.

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>Observaciones

La `RoInitializeWrapper` clase `Windows::Foundation::Uninitialize()`invoca .
