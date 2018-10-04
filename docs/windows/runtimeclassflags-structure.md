---
title: RuntimeClassFlags (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c5bfd9fc6dd87c61149722e8ef7fed79f8f017da
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788843"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags (estructura)

Contiene el tipo de una instancia de un [RuntimeClass](../windows/runtimeclass-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parámetros

*flags*<br/>
Un [RuntimeClassType (enumeración)](../windows/runtimeclasstype-enumeration.md) valor.

## <a name="members"></a>Miembros

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[RuntimeClassFlags::value (constante)](#value-constant)|Contiene un [RuntimeClassType (enumeración)](../windows/runtimeclasstype-enumeration.md) valor.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RuntimeClassFlags`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="value-constant"></a>Runtimeclassflags (constante)

Un campo que contenga un [RuntimeClassType (enumeración)](../windows/runtimeclasstype-enumeration.md) valor.
  
```cpp
static const unsigned int value = flags;
```
