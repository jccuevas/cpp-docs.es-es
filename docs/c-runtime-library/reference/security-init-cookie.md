---
title: __security_init_cookie | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __security_init_cookie
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- security_init_cookie
- __security_init_cookie
dev_langs:
- C++
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 699a75da7829feb39142a777a34a14fcd85be653
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821150"
---
# <a name="securityinitcookie"></a>__security_init_cookie

Inicializa la cookie de seguridad global.

## <a name="syntax"></a>Sintaxis

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Comentarios

La cookie de seguridad global se usa para la protección de saturación del búfer en el código compilado con [/GS (Comprobación de seguridad del búfer)](../../build/reference/gs-buffer-security-check.md) y en el código que usa el control de excepciones. En la entrada a una función con protección de saturación, la cookie se coloca en la pila y, en la salida, el valor de la pila se compara con la cookie global. Cualquier diferencia en la comparación indica que se ha producido una saturación del búfer y da lugar a la finalización inmediata del programa.

Normalmente, **__security_init_cookie** llama a CRT cuando se inicializa. Si se omite la inicialización de CRT, por ejemplo, si usa [/Entry](../../build/reference/entry-entry-point-symbol.md) para especificar un punto de entrada, debe llamarlo **__security_init_cookie** usted mismo. Si **__security_init_cookie** no se llama, global de la cookie de seguridad se establece en un valor predeterminado y se pone en peligro la protección de saturación del búfer. Dado que un atacante puede aprovechar este valor de cookie predeterminado para invalidar las comprobaciones de saturación del búfer, se recomienda que siempre llame a **__security_init_cookie** al definir su propio punto de entrada.

La llamada a **__security_init_cookie** deben realizarse antes que cualquier protección de saturación se introduce la función; en caso contrario, se detectará una saturación del búfer falsa. Para obtener más información, vea [C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) (Error de tiempo de ejecución de C R6035).

## <a name="example"></a>Ejemplo

Vea los ejemplos de [C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) (Error de tiempo de ejecución de C R6035).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie** es una extensión de Microsoft para la biblioteca en tiempo de ejecución de C estándar. Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Microsoft Security Response Center](https://www.microsoft.com/msrc?rtc=1)
