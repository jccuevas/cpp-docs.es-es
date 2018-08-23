---
title: RuntimeClassFlags (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassFlags structure
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f0a32fc373900af1a4322f4f2511c44417d2916a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594279"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags (estructura)

Contiene el tipo de una instancia de un [RuntimeClass](../windows/runtimeclass-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <
   unsigned int flags
>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Parámetros

*flags*  
Un [RuntimeClassType (enumeración)](../windows/runtimeclasstype-enumeration.md) valor.

## <a name="members"></a>Miembros

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[RuntimeClassFlags::value (constante)](../windows/runtimeclassflags-value-constant.md)|Contiene un [RuntimeClassType (enumeración)](../windows/runtimeclasstype-enumeration.md) valor.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`RuntimeClassFlags`

## <a name="requirements"></a>Requisitos

**Encabezado:** implements.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)