---
title: Acceso a argumentos
ms.date: 04/04/2018
f1_keywords:
- c.arguments
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
ms.openlocfilehash: 8107cffa6a2da41c38b116b2e3fe36adf6ac945f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470413"
---
# <a name="argument-access"></a>Acceso a argumentos

Las macros **va_arg**, **va_end** y **va_start** proporcionan acceso a argumentos de función cuando el número de argumentos es variable. Estas macros se definen en \<stdarg.h> para la compatibilidad con ANSI/ISO C y en \<varargs.h> para la compatibilidad con System V de UNIX.

## <a name="argument-access-macros"></a>Macros de acceso a argumentos

|Macro|Usar|
|-----------|-------------------------------|
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Recuperar argumentos de una lista|
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Restablecer el puntero|
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Establecer el puntero al principio de la lista de argumentos|

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)
