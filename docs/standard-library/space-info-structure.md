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
ms.openlocfilehash: 3506572586f0dc8edc3f9e97955e7612bcea46ae
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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
[space](http://msdn.microsoft.com/en-us/7fce0b0e-523b-4598-b218-47245d0204ca)<br/>
[Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)<br/>
