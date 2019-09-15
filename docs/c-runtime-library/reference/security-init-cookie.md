---
title: __security_init_cookie
ms.date: 11/04/2016
api_name:
- __security_init_cookie
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: 9f7e9924f4a96803749418d777e5ee2020f9df78
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948717"
---
# <a name="__security_init_cookie"></a>__security_init_cookie

Inicializa la cookie de seguridad global.

## <a name="syntax"></a>Sintaxis

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Comentarios

La cookie de seguridad global se usa para la protección de saturación del búfer en el código compilado con [/GS (Comprobación de seguridad del búfer)](../../build/reference/gs-buffer-security-check.md) y en el código que usa el control de excepciones. En la entrada a una función con protección de saturación, la cookie se coloca en la pila y, en la salida, el valor de la pila se compara con la cookie global. Cualquier diferencia en la comparación indica que se ha producido una saturación del búfer y da lugar a la finalización inmediata del programa.

Normalmente, el CRT llama a **__security_init_cookie** cuando se inicializa. Si omite la inicialización de CRT (por ejemplo, si usa [/entry](../../build/reference/entry-entry-point-symbol.md) para especificar un punto de entrada), debe llamar a **__security_init_cookie** . Si no se llama a **__security_init_cookie** , la cookie de seguridad global se establece en un valor predeterminado y se pone en peligro la protección de saturación del búfer. Dado que un atacante puede aprovechar este valor de cookie predeterminado para derrotar las comprobaciones de saturación del búfer, se recomienda llamar siempre a **__security_init_cookie** al definir su propio punto de entrada.

La llamada a **__security_init_cookie** debe realizarse antes de que se especifique cualquier función de protección contra saturación. de lo contrario, se detectará una saturación del búfer falsa. Para obtener más información, vea [C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) (Error de tiempo de ejecución de C R6035).

## <a name="example"></a>Ejemplo

Vea los ejemplos de [C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) (Error de tiempo de ejecución de C R6035).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__security_init_cookie** es una extensión de Microsoft para la biblioteca en tiempo de ejecución estándar de C. Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Centro de respuestas de seguridad de Microsoft](https://www.microsoft.com/msrc?rtc=1)
