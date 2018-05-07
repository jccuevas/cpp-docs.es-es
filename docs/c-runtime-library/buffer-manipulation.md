---
title: Manipulación del búfer | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aaa85b3e3f0730a564ac1aff3e74f58cef20356a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="buffer-manipulation"></a>Manipulación del búfer

Utilice estas rutinas para trabajar con áreas de memoria en forma de byte a byte.

## <a name="buffer-manipulation-routines"></a>Rutinas de manipulación del búfer

|Rutina|Usar|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|Copiar los caracteres de un búfer en el otro hasta que se haya copiado el carácter definido o el número de caracteres determinado|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Devolver el puntero a la primera aparición en el búfer del carácter especificado dentro de un número especificado de caracteres|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Comparar el número especificado de caracteres de dos búferes|
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s, wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Copiar el número especificado de caracteres de un búfer a otro|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Comparar el número especificado de caracteres de dos búferes sin distinción entre mayúsculas y minúsculas|
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s, wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Copiar el número especificado de caracteres de un búfer a otro|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Utilizar el carácter especificado para inicializar el número especificado de bytes en el búfer|
|[_swab](../c-runtime-library/reference/swab.md)|Intercambiar bytes de datos y almacenarlos en una ubicación especificada|

Cuando las áreas de origen y de destino se superponen, solo se garantiza que **memmove** copie el origen completo correctamente.

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)
