---
title: longjmp
ms.date: 08/14/2018
api_name:
- longjmp
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: b4527a29475f9e393dc5abf19b866d926bec2ccc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953144"
---
# <a name="longjmp"></a>longjmp

Restaura el entorno de pila y la configuración regional de ejecución establecida por `setjmp` una llamada.

## <a name="syntax"></a>Sintaxis

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parámetros

*env*<br/>
Variable donde se almacena el entorno.

*value*<br/>
Valor que se devolverá a la llamada a `setjmp`.

## <a name="remarks"></a>Comentarios

La función **longjmp** restaura un entorno de pila y la configuración regional de ejecución guardada previamente en `setjmp` *env* by. `setjmp`y **longjmp** proporcionan una manera de ejecutar un método **goto**no local; normalmente se utilizan para pasar el control de la ejecución al control de errores o al código de recuperación en una rutina llamada anteriormente sin usar las convenciones de llamada y devolución normales.

Una llamada a `setjmp` hace que el entorno de pila actual se guarde en *env*. Una llamada subsiguiente a **longjmp** restaura el entorno guardado y devuelve el control al punto inmediatamente posterior a la llamada correspondiente `setjmp` . La ejecución se reanuda como si se hubiera devuelto *value* mediante la llamada `setjmp`. Los valores de todas las variables (excepto las variables de registro) que son accesibles para el control de recepción de rutina contienen los valores que tenían cuando se llamó a **longjmp** . Los valores de las variables de registro son imprevisibles. El valor devuelto por `setjmp` debe ser distinto de cero. Si *value* se pasa como 0, se sustituye el valor 1 en la devolución real.

**Específicos de Microsoft**

En Microsoft C++ Code en Windows, **longjmp** usa la misma semántica de desenredo de pila que el código de control de excepciones. Es seguro usar en los mismos lugares en los que C++ se pueden generar excepciones. Sin embargo, este uso no es portable e incluye algunas advertencias importantes.

Llame solo a **longjmp** antes de que la `setjmp` función a la que llamó devuelve; de lo contrario, los resultados son imprevisibles.

Observe las siguientes restricciones al usar **longjmp**:

- No presuponga que los valores de las variables de registro seguirán siendo los mismos. Es posible que los valores de las variables Register `setjmp` de la rutina que realiza la llamada no se restauren a los valores correctos después de que se ejecute **longjmp** .

- No use **longjmp** para transferir el control fuera de una rutina de control de interrupciones a menos que la interrupción se deba a una excepción de punto flotante. En este caso, un programa puede devolver desde un controlador de interrupción a través de **longjmp** si primero reinicializa el paquete matemático de punto flotante llamando a [_fpreset](fpreset.md).

- No use **longjmp** para transferir el control de una rutina de devolución de llamada invocada directa o indirectamente por el código de Windows.

- Si el código se compila mediante **/EHS** o **/EHsc** y la función que contiene la llamada a **longjmp** es **noexception** , es posible que los objetos locales de esa función no se destruyan durante el desenredado de la pila.

**FIN de Específicos de Microsoft**

> [!NOTE]
> En código C++ portable, no se puede `setjmp` asumir `longjmp` y C++ admitir la semántica de objetos. En concreto, `setjmp` un / `longjmp` `longjmp` pardellamadastieneuncomportamientoindefinidosialreemplazaryCatchyThrowseinvocaríanlosdestructoresnotrivialesparalosobjetosautomáticos`setjmp` . En C++ los programas, se recomienda usar el C++ mecanismo de control de excepciones.

Para obtener más información, vea [Usar setjmp/longjmp](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_pfreset](fpreset.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
