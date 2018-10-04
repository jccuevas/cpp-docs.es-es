---
title: RoInitializeWrapper (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22271435db3a66095da5b6065a6b9cc9463b3de2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233754"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper (Clase)

Inicializa el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```cpp
class RoInitializeWrapper
```

## <a name="remarks"></a>Comentarios

`RoInitializeWrapper` es una ventaja que inicializa el tiempo de ejecución de Windows y devuelve un HRESULT que indica si la operación fue correcta. Dado que el destructor de clase llama a `::Windows::Foundation::Uninitialize`, las instancias de `RoInitializeWrapper` debe declararse en el ámbito global o de nivel superior.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                                                    | Descripción
----------------------------------------------------------------------- | -----------------------------------------------------------------
[Roinitializewrapper](#roinitializewrapper)        | Inicializa una nueva instancia de la clase `RoInitializeWrapper`.
[RoInitializeWrapper:: ~ RoInitializeWrapper](#tilde-roinitializewrapper) | Destruye la instancia actual de la `RoInitializeWrapper` clase.

### <a name="public-operators"></a>Operadores públicos

Name                                       | Descripción
------------------------------------------ | ------------------------------------------------------------------------
[::HRESULT()](#hresult) | Recupera el valor HRESULT producido por la `RoInitializeWrapper` constructor.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RoInitializeWrapper`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="hresult"></a>::HRESULT()

Recupera el valor HRESULT producido por la última `RoInitializeWrapper` constructor.

```cpp
operator HRESULT()  
```

## <a name="roinitializewrapper"></a>Roinitializewrapper

Inicializa una nueva instancia de la clase `RoInitializeWrapper`.

```cpp
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```

### <a name="parameters"></a>Parámetros

*flags*<br/>
Una de las enumeraciones RO_INIT_TYPE, que especifica la compatibilidad proporcionada por el tiempo de ejecución de Windows.

### <a name="remarks"></a>Comentarios

El `RoInitializeWrapper` clase invoca `Windows::Foundation::Initialize(flags)`.

## <a name="tilde-roinitializewrapper"></a>RoInitializeWrapper:: ~ RoInitializeWrapper

Desinicializa el tiempo de ejecución de Windows.

```cpp
~RoInitializeWrapper()  
```

### <a name="remarks"></a>Comentarios

El `RoInitializeWrapper` clase invoca `Windows::Foundation::Uninitialize()`.
