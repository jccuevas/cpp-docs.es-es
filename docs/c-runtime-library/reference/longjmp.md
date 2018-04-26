---
title: longjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a593c2dcdfe1731ee5c6438c7a330e7f4ea8740
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="longjmp"></a>longjmp

Restaura el entorno de pila y la configuración regional de ejecución.

## <a name="syntax"></a>Sintaxis

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parámetros

*env* variables de entorno en el que se almacena.

*valor* valor que se devolverá a **setjmp** llamar.

## <a name="remarks"></a>Comentarios

El **longjmp** función restaura un escenario de entorno y la ejecución de pila previamente guardado en *env* por **setjmp**. **setjmp** y **longjmp** proporcionan una manera de ejecutar un no locales **goto**; normalmente se usan para pasar el control de ejecución a código de control de errores o de recuperación en una rutina invocada anteriormente sin con la normal llame y convenciones de devolución.

Una llamada a **setjmp** hace que el entorno de pila actual se guarde en *env*. Una llamada subsiguiente a **longjmp** restaura el entorno guardado y devuelve el control al punto inmediatamente posterior a la correspondiente **setjmp** llamar. Reanuda la ejecución como si *valor* solo había sido devuelto por la **setjmp** llamar. Los valores de todas las variables (excepto variables de registro) que se puede acceder a la rutina de recibir el control contienen los valores que tenían cuando **longjmp** se llamó. Los valores de las variables de registro son imprevisibles. El valor devuelto por **setjmp** debe ser distinto de cero. Si *value* se pasa como 0, se sustituye el valor 1 en la devolución real.

Llame a **longjmp** antes de la función que llamó **setjmp** devuelva el control; en caso contrario, los resultados son imprevisibles.

Observe las siguientes restricciones al utilizar **longjmp**:

- No presuponga que los valores de las variables de registro seguirán siendo los mismos. Los valores de variables de registro de la rutina que realiza la llamada **setjmp** no se pueden restaurar a los valores adecuados después **longjmp** se ejecuta.

- No utilice **longjmp** para transferir el control fuera de una rutina de control de interrupción a menos que la interrupción sea consecuencia de una excepción de punto flotante. En este caso, puede devolver un programa desde un controlador de interrupción a través de **longjmp** si se reinicializa primero el paquete matemático de punto flotante mediante una llamada a **_fpreset**.

     **Tenga en cuenta** tenga precaución al utilizar **setjmp** y **longjmp** en programas de C++. Dado que estas funciones no admiten la semántica de objetos de C++, es más seguro usar el mecanismo de control de excepciones de C++.

Para obtener más información, vea [Usar setjmp/longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_pfreset](fpreset.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)<br/>
