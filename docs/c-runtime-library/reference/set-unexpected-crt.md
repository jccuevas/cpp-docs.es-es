---
title: set_unexpected (CRT)
ms.date: 11/04/2016
apiname:
- set_unexpected
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
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: 6c38421e447ca7b3f263148f51f0ade5c59e2804
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484232"
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

Instala su propia función de finalización a la que debe llamar **unexpected**.

## <a name="syntax"></a>Sintaxis

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Parámetros

*unexpFunction*<br/>
Puntero a una función que se escribe para reemplazar el **inesperado** función.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función de finalización anterior registrado por **_set_unexpected** para que la función anterior se puede restaurar más adelante. Si no se ha establecido ninguna función anterior, el valor devuelto puede utilizarse para restaurar el comportamiento predeterminado; Este valor puede ser **NULL**.

## <a name="remarks"></a>Comentarios

El **set_unexpected** función instalaciones *unexpFunction* como la función llamada por **inesperado**. **inesperado** no se utiliza en la implementación actual del control de excepciones de C++. El **unexpected_function** tipo está definido en el controlador de eventos. H como un puntero a una función inesperada definida por el usuario, *unexpFunction* que devuelve **void**. Personalizado *unexpFunction* función no debe devolver al llamador.

```cpp
typedef void ( *unexpected_function )( );
```

De forma predeterminada, **inesperado** llamadas **finalizar**. Puede cambiar este comportamiento predeterminado escribiendo su propia función de finalización y llamar a **set_unexpected** con el nombre de la función como su argumento. **inesperado** llama a la última función especificada como argumento a **set_unexpected**.

A diferencia de la función de terminación personalizada instalada mediante una llamada a **set_terminate**, se puede producir una excepción desde *unexpFunction*.

En un entorno multiproceso, las funciones inesperadas se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función inesperada. Por lo tanto, cada subproceso se encarga de su propio control inesperado.

En la implementación actual de Microsoft de control de excepciones de C++, **inesperado** llamadas **finalizar** de forma predeterminada y nunca se llamará a la biblioteca de tiempo de ejecución del control de excepciones. No hay ninguna ventaja particular que realiza la llamada **inesperado** lugar **finalizar**.

Solo hay un **set_unexpected** controlador para todos los dinámicamente exe y DLL vinculados; incluso si se llama a **set_unexpected** el controlador puede reemplazarse por otro o que va a reemplazar un controlador establecido por otro archivo DLL o EXE.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
