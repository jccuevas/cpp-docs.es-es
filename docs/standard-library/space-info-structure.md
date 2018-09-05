---
title: space_info (Estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::space_info
dev_langs:
- C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0f1eb9818356e7261125efaea69e275c3e29b8
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684688"
---
# <a name="spaceinfo-structure"></a>space_info (Estructura)

Contiene información sobre un volumen.

## <a name="syntax"></a>Sintaxis

```cpp
struct space_info   {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };
```

## <a name="members"></a>Miembros

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|`unsigned long long available`|Representa el número de bytes que están disponibles para representar datos en el volumen.|
|`unsigned long long capacity`|Representa el número total de bytes que el volumen puede representar.|
|`unsigned long long free`|Representa el número de bytes que no se usan para representar datos en el volumen.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<filesystem >

**Espacio de nombres:** std::experimental::filesystem

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)<br/>
