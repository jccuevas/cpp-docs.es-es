---
title: Acceso a argumentos | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.arguments
dev_langs:
- C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38d4031fcfba793a99688b6fd1cc91a3f1519989
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
