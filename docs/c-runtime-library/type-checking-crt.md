---
title: Comprobación de tipos (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.types
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
ms.openlocfilehash: bb5aecc2b47aa8e88666f42d8022395bf99fd85e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747688"
---
# <a name="type-checking-crt"></a>Comprobación de tipos (CRT)

El compilador realiza una comprobación de tipos limitada de las funciones que pueden usar un número variable de argumentos, como sigue:

|Llamada a función|Argumentos con tipos comprobados|
|-------------------|-----------------------------|
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|Primer argumento (cadena de formato)|
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|Primeros dos argumentos (archivo o búfer y cadena de formato)|
|`_snprintf_s`|Primeros tres argumentos (archivo o búfer, recuento y cadena de formato)|
|`_open`|Primeros dos argumentos (ruta de acceso y marca `_open`)|
|`_sopen_s`|Primeros tres argumentos (ruta de acceso, marca `_open` y modo compartido)|
|`_execl`, `_execle`, `_execlp`, `_execlpe`|Primeros dos argumentos (ruta de acceso y primer puntero de argumento)|
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|Primeros tres argumentos (marca de modo, ruta de acceso y primer puntero de argumento)|

El compilador realiza la misma comprobación de tipo limitada en los homólogos de caracteres anchos de estas funciones.

## <a name="see-also"></a>Vea también

[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
