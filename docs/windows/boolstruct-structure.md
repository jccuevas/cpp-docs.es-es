---
title: BoolStruct (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
dev_langs:
- C++
helpviewer_keywords:
- BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4981c7f82fe2c544bf907ac59d6e9ca22105cbd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592542"
---
# <a name="boolstruct-structure"></a>BoolStruct (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Comentarios

El **BoolStruct** estructura define si un `ComPtr` administra la duración del objeto de una interfaz. **BoolStruct** usa internamente el [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operador.

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[BoolStruct::Member (miembro de datos)](../windows/boolstruct-member-data-member.md)|Especifica que un [ComPtr](../windows/comptr-class.md) es o no, es administrar la vigencia del objeto de una interfaz.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BoolStruct`

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)  
[ComPtr::operator Microsoft::WRL::Details::BoolType (operador)](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)