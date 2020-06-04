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
ms.openlocfilehash: 9fed5bb31b077288495a78aefcbd8401b3520bb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367226"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags (estructura)

Contiene el tipo de una instancia de [RuntimeClass](runtimeclass-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parámetros

*Banderas*<br/>
Un [RuntimeClassType (valor) de la enumeración.](runtimeclasstype-enumeration.md)

## <a name="members"></a>Miembros

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[RuntimeClassFlags::value (Constante)](#value-constant)|Contiene un [RuntimeClassType (valor)](runtimeclasstype-enumeration.md) .|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RuntimeClassFlags`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="runtimeclassflagsvalue-constant"></a><a name="value-constant"></a>RuntimeClassFlags::value Constante

Campo que contiene un valor [RuntimeClassType Enumeration.](runtimeclasstype-enumeration.md)

```cpp
static const unsigned int value = flags;
```
