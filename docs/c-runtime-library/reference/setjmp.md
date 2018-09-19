---
title: setjmp | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
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
ms.openlocfilehash: 0bd7d57d0678744243356a0565e10cbe4065f8d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032547"
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

Devuelve 0 después de guardar el entorno de pila. Si **setjmp** devuelve como resultado de una `longjmp` llamar a, devuelve el *valor* argumento de `longjmp`, o si el *valor* argumento de `longjmp` es 0, **setjmp** devuelve 1. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

El **setjmp** función guarda un entorno de pila, que puede restaurar posteriormente usando `longjmp`. Cuando se usan juntos, **setjmp** y `longjmp` proporcionan una forma de ejecutar un no locales **goto**. Se utilizan normalmente para pasar el control de la ejecución al control de errores o al código de recuperación en una rutina invocada anteriormente sin utilizar convenciones habituales de llamada o devolución.

Una llamada a **setjmp** guarda el entorno de pila actual en *env*. Una llamada subsiguiente a `longjmp` restaura el entorno guardado y devuelve el control al punto justo después de la correspondiente **setjmp** llamar. Todas las variables (excepto las variables de registro) a las que se puede obtener acceso en la rutina que recibe el control contienen los valores que tenían cuando se llamó a `longjmp`.

No es posible usar **setjmp** para pasar del código nativo a código administrado.

**Específicos de Microsoft**

En el código de C++ de Microsoft en Windows, **longjmp** usa la misma semántica de desenredo de pila como código de control de excepciones. Es seguro utilizar en los mismos lugares que se pueden producir excepciones de C++. Sin embargo, este uso no es portátil y viene con algunas advertencias importantes. Para obtener más información, consulte [longjmp](longjmp.md).

**FIN de Específicos de Microsoft**

> [!NOTE]
> En el código C++ portátil, no puede suponer `setjmp` y `longjmp` admiten la semántica de objeto de C++. En concreto, un `setjmp` / `longjmp` llamada par tiene un comportamiento indefinido si se reemplaza el `setjmp` y `longjmp` por **catch** y **throw** invocaría los destructores no triviales para los objetos automáticos. En programas de C++, se recomienda que usar el mecanismo de control de excepciones de C++.

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
[longjmp](longjmp.md)
