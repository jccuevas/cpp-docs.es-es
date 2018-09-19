---
title: TypeCode (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::TypeCode
dev_langs:
- C++
helpviewer_keywords:
- Platform::TypeCode Enumeration
ms.assetid: 93c1305f-eb16-4bec-aead-f88d9518b4cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb19a922655a77a2f7a2b5806c9b721f17e028f8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104178"
---
# <a name="platformtypecode-enumeration"></a>Platform::TypeCode (Enumeración)

Especifica una categoría numérica que representa un tipo integrado.

## <a name="syntax"></a>Sintaxis

```cpp
enum class TypeCode {};
```

### <a name="members"></a>Miembros

|Código de tipo|Descripción|
|---------------|-----------------|
|Booleano|Tipo de Platform::Boolean|
|Char16|Tipo de default::char16.|
|DateTime|Tipo DateTime.|
|Decimal|Tipo numérico.|
|Doble|Tipo de default::float64.|
|Empty|Void|
|Int16|Tipo de default::int16.|
|Int32|Tipo de default::int32.|
|Int64|Tipo de default::int64.|
|Int8|Tipo de default::int8.|
|Object|Tipo de Platform::Object.|
|Single|Tipo de default::float32.|
|String|Tipo de Platform::String.|
|UInt16|Tipo de default::uint16.|
|UInt32|Tipo de default::uint32.|
|UInt64|Tipo de default::uint64.|
|UInt8|Tipo de default::uint8.|

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres:** Plataforma

**Metadatos:** platform.winmd