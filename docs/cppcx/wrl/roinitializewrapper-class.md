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
ms.openlocfilehash: b43d5bb2f553d298584ab2ae497c22637d3beb0d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58785767"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper (Clase)

Inicializa el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Comentarios

`RoInitializeWrapper` es una ventaja que inicializa el tiempo de ejecución de Windows y devuelve un HRESULT que indica si la operación fue correcta. Dado que el destructor de clase llama a `::Windows::Foundation::Uninitialize`, las instancias de `RoInitializeWrapper` debe declararse en el ámbito global o de nivel superior.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                                    | Descripción
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | Inicializa una nueva instancia de la clase `RoInitializeWrapper`.
[RoInitializeWrapper::~RoInitializeWrapper](#tilde-roinitializewrapper) | Destruye la instancia actual de la `RoInitializeWrapper` clase.

### <a name="public-operators"></a>Operadores públicos

Name                                       | Descripción
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | Recupera el valor HRESULT producido por la `RoInitializeWrapper` constructor.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RoInitializeWrapper`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="hresult"></a>RoInitializeWrapper::HRESULT()

Recupera el valor HRESULT producido por la última `RoInitializeWrapper` constructor.

```cpp
operator HRESULT()
```

## <a name="roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

Inicializa una nueva instancia de la clase `RoInitializeWrapper`.

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>Parámetros

*flags*<br/>
Una de las enumeraciones RO_INIT_TYPE, que especifica la compatibilidad proporcionada por el tiempo de ejecución de Windows.

### <a name="remarks"></a>Comentarios

El `RoInitializeWrapper` clase invoca `Windows::Foundation::Initialize(flags)`.

## <a name="tilde-roinitializewrapper"></a>RoInitializeWrapper::~RoInitializeWrapper

Desinicializa el tiempo de ejecución de Windows.

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>Comentarios

El `RoInitializeWrapper` clase invoca `Windows::Foundation::Uninitialize()`.
