---
title: RuntimeClassFlags (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 4cbd3f367bc57c2eedf672422a458b67b1908fc0
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785852"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags (estructura)

Contiene el tipo de una instancia de un [RuntimeClass](runtimeclass-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parámetros

*flags*<br/>
Un [RuntimeClassType (enumeración)](runtimeclasstype-enumeration.md) valor.

## <a name="members"></a>Miembros

### <a name="public-constants"></a>Constantes públicas

|Name|Descripción|
|----------|-----------------|
|[RuntimeClassFlags::value (constante)](#value-constant)|Contiene un [RuntimeClassType (enumeración)](runtimeclasstype-enumeration.md) valor.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RuntimeClassFlags`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres**: Microsoft::WRL

## <a name="value-constant"></a>Runtimeclassflags (constante)

Un campo que contenga un [RuntimeClassType (enumeración)](runtimeclasstype-enumeration.md) valor.

```cpp
static const unsigned int value = flags;
```
