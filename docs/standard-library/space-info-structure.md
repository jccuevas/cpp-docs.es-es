---
title: space_info (Estructura)
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::space_info
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
ms.openlocfilehash: 2a9856746a8bbc796871663a81bd8911d34dcd4a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457554"
---
# <a name="spaceinfo-structure"></a>space_info (Estructura)

Contiene información sobre un volumen.

## <a name="syntax"></a>Sintaxis

```cpp
struct space_info
{
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
};
```

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`unsigned long long capacity`|Representa el número total de bytes que el volumen puede representar.|
|`unsigned long long free`|Representa el número de bytes que no se usan para representar datos en el volumen.|
|`unsigned long long available`|Representa el número de bytes que están disponibles para representar datos en el volumen.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> filesystem

**Espacio de nombres:** std::experimental::filesystem

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)
