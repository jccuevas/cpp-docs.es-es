---
title: setjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- setjmp
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
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc4673485577f5a12024d31e94063c82a8c7b8c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407257"
---
# <a name="setjmp"></a>setjmp

Guarda el estado actual del programa.

## <a name="syntax"></a>Sintaxis

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>Parámetros

*env*<br/>
Variable donde se almacena el entorno.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 después de guardar el entorno de pila. Si **setjmp** devuelve como resultado de un **longjmp** llamar a, devuelve el **valor** argumento de **longjmp**, o si la **valor**  argumento de **longjmp** es 0, **setjmp** devuelve 1. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

El **setjmp** función guarda un entorno de pila, que posteriormente pueda restaurar, con **longjmp**. Cuando se usan juntos, **setjmp** y **longjmp** proporcionan una manera de ejecutar un no locales **goto**. Se utilizan normalmente para pasar el control de la ejecución al control de errores o al código de recuperación en una rutina invocada anteriormente sin utilizar convenciones habituales de llamada o devolución.

Una llamada a **setjmp** guarda el entorno de pila actual en *env*. Una llamada subsiguiente a **longjmp** restaura el entorno guardado y devuelve el control al punto justo después de la correspondiente **setjmp** llamar. Todas las variables (excepto las variables de register) puede tener acceso a la rutina de recibir el control contienen los valores que tenían cuando **longjmp** se llamó.

No es posible utilizar **setjmp** para saltar de código nativo a código administrado.

**Tenga en cuenta** **setjmp** y **longjmp** no admitan la semántica de objetos de C++. En los programas de C++, use el mecanismo de control de excepciones de C++.

Para obtener más información, vea [Usar setjmp/longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_pfreset](fpreset.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)<br/>
[_setjmp3](../../c-runtime-library/setjmp3.md)<br/>
