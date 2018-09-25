---
title: ModuleBase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
dev_langs:
- C++
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a87b5d617663e87e8c69596e6b1eedca61996b80
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169559"
---
# <a name="modulebase-class"></a>ModuleBase (Clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Comentarios

Representa la clase base de la [módulo](../windows/module-class.md) clases.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                         | Descripción
-------------------------------------------- | ---------------------------------------------------------
[Modulebase](#modulebase)        | Inicializa una instancia de la clase `Module`.
[ModuleBase:: ~ ModuleBase](#tilde-modulebase) | Desinicializa la instancia actual de la `Module` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                                      | Descripción
--------------------------------------------------------- | -------------------------------------------------------------------------
[Modulebase](#decrementobjectcount) | Cuando se implementa, disminuye el número de objetos que sigue el módulo.
[Modulebase](#incrementobjectcount) | Cuando se implementa, incrementa el número de objetos que se hace un seguimiento mediante el módulo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ModuleBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Namespace:** wrl

## <a name="tilde-modulebase"></a>ModuleBase:: ~ ModuleBase

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Comentarios

Desinicializa la instancia actual de la `ModuleBase` clase.

## <a name="decrementobjectcount"></a>Modulebase

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Valor devuelto

El recuento antes de la operación de decremento.

### <a name="remarks"></a>Comentarios

Cuando se implementa, disminuye el número de objetos que sigue el módulo.

## <a name="incrementobjectcount"></a>Modulebase

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Valor devuelto

El recuento antes de la operación de incremento.

### <a name="remarks"></a>Comentarios

Cuando se implementa, incrementa el número de objetos que se hace un seguimiento mediante el módulo.

## <a name="modulebase"></a>Modulebase

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Comentarios

Inicializa una instancia de la clase `Module`.
