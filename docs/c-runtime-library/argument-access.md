---
title: Acceso a argumentos | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afef1300637f7a31755eb9408f9d33d9504475a1
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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
