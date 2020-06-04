---
title: setjmp
ms.date: 08/14/2018
api_name:
- setjmp
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
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 4a88467f5b94ceae4281a35f1486380a877be2e5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948235"
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

Devuelve 0 después de guardar el entorno de pila. Si **setjmp** devuelve como `longjmp` resultado de una llamada a, devuelve el argumento *de valor* de `longjmp`, o si el argumento de *valor* de `longjmp` es 0, **setjmp** devuelve 1. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

La función **setjmp** guarda un entorno de pila, que posteriormente se puede restaurar mediante `longjmp`. Cuando se usan juntos , setjmp `longjmp` y proporcionan una forma de ejecutar un método **goto**no local. Se utilizan normalmente para pasar el control de la ejecución al control de errores o al código de recuperación en una rutina invocada anteriormente sin utilizar convenciones habituales de llamada o devolución.

Una llamada a **setjmp** guarda el entorno de pila actual en *env*. Una llamada subsiguiente a `longjmp` restaura el entorno guardado y devuelve el control al punto inmediatamente posterior a la llamada **setjmp** correspondiente. Todas las variables (excepto las variables de registro) a las que se puede obtener acceso en la rutina que recibe el control contienen los valores que tenían cuando se llamó a `longjmp`.

No es posible usar **setjmp** para saltar de código nativo a código administrado.

**Específicos de Microsoft**

En Microsoft C++ Code en Windows, **longjmp** usa la misma semántica de desenredo de pila que el código de control de excepciones. Es seguro usar en los mismos lugares en los que C++ se pueden generar excepciones. Sin embargo, este uso no es portable e incluye algunas advertencias importantes. Para obtener más información, consulte [longjmp](longjmp.md).

**FIN de Específicos de Microsoft**

> [!NOTE]
> En código C++ portable, no se puede `setjmp` asumir `longjmp` y C++ admitir la semántica de objetos. En concreto, `setjmp` un / `longjmp` `longjmp` pardellamadastieneuncomportamientoindefinidosialreemplazaryCatchyThrowseinvocaríanlosdestructoresnotrivialesparalosobjetosautomáticos`setjmp` . En C++ los programas, se recomienda usar el C++ mecanismo de control de excepciones.

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
