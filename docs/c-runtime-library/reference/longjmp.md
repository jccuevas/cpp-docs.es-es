---
title: longjmp | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- longjmp
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
- longjmp
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 857fae2e9c38dfe2c5cd468c6d1b50c6fdd2f317
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2018
ms.locfileid: "42575534"
---
# <a name="longjmp"></a>longjmp

Restaura la pila ejecución y el entorno de configuración regional establecida un `setjmp` llamar.

## <a name="syntax"></a>Sintaxis

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parámetros

*env*  
Variable donde se almacena el entorno.

*valor*  
Valor que se devolverá a la llamada a `setjmp`.

## <a name="remarks"></a>Comentarios

El **longjmp** función restaura un escenario de entorno y la ejecución de pila previamente guardado en *env* por `setjmp`. `setjmp` y **longjmp** proporcionan una forma de ejecutar un valor **goto**; normalmente se usan para pasar el control de ejecución al código de control de errores o de recuperación en una rutina invocada anteriormente sin utilizar la llamada normal y convenciones de devolución.

Una llamada a `setjmp` hace que el entorno de pila actual se guarde en *env*. Una llamada subsiguiente a **longjmp** restaura el entorno guardado y devuelve el control al punto inmediatamente posterior a la correspondiente `setjmp` llamar. La ejecución se reanuda como si se hubiera devuelto *value* mediante la llamada `setjmp`. Los valores de todas las variables (excepto las variables de registro) que se puede acceder a la rutina que recibe el control contienen los valores que tenían cuando **longjmp** llamó. Los valores de las variables de registro son imprevisibles. El valor devuelto por `setjmp` debe ser distinto de cero. Si *value* se pasa como 0, se sustituye el valor 1 en la devolución real.

**Específicos de Microsoft**

En el código de C++ de Microsoft en Windows, **longjmp** usa la misma semántica de desenredo de pila como código de control de excepciones. Es seguro utilizar en los mismos lugares que se pueden producir excepciones de C++. Sin embargo, este uso no es portátil y viene con algunas advertencias importantes.

Solo llame a **longjmp** antes de la función que llamó `setjmp` devuelve; en caso contrario, los resultados son impredecibles.

Observe las siguientes restricciones al usar **longjmp**:

- No presuponga que los valores de las variables de registro seguirán siendo los mismos. Los valores de variables de registro en la rutina que llama a `setjmp` no pueden restaurarse a los valores adecuados después **longjmp** se ejecuta.

- No use **longjmp** para transferir el control fuera de una rutina de control de interrupción a menos que la interrupción sea consecuencia de una excepción de punto flotante. En este caso, podría devolver un programa desde un controlador de interrupción a través de **longjmp** si primero se reinicializa el paquete matemático de punto flotante mediante una llamada a [_fpreset](fpreset.md).

- No use **longjmp** para transferir el control de una rutina de devolución de llamada invocada directa o indirectamente por código de Windows.

- Si el código compilado mediante **/EHs** o **/EHsc** y la función que contiene el **longjmp** llamada es **noexcept** objetos locales, a continuación, en el que la función no se destruyan durante el desenredo de pila.

**FIN de Específicos de Microsoft**

> [!NOTE]  
> En el código C++ portátil, no puede suponer `setjmp` y `longjmp` admiten la semántica de objeto de C++. En concreto, un `setjmp` / `longjmp` llamada par tiene un comportamiento indefinido si se reemplaza el `setjmp` y `longjmp` por **catch** y **throw** invocaría los destructores no triviales para los objetos automáticos. En programas de C++, se recomienda que usar el mecanismo de control de excepciones de C++.

Para obtener más información, vea [Usar setjmp/longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_pfreset](fpreset.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)  
[setjmp](setjmp.md)  
