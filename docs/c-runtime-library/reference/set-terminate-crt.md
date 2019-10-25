---
title: set_terminate (CRT)
ms.date: 11/04/2016
api_name:
- set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 860789a3f2fda5ef13cadffa2a00dba4fbd2090a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948370"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Instala su propia rutina de finalización a la que debe llamar **Terminate**.

## <a name="syntax"></a>Sintaxis

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parámetros

*termFunction*<br/>
Puntero a una función de finalización que se escribe.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función anterior registrada por **set_terminate** para que la función anterior se pueda restaurar más adelante. Si no se ha establecido ninguna función anterior, el valor devuelto se puede utilizar para restaurar el comportamiento predeterminado; Este valor puede ser **null**.

## <a name="remarks"></a>Comentarios

La función **set_terminate** instala *termFunction* como la función a la que llama **Terminate**. **set_terminate** se usa con C++ el control de excepciones y se puede llamar en cualquier punto del programa antes de que se produzca la excepción. la instrucción **Terminate** llama a [Abort](abort.md) de forma predeterminada. Puede cambiar este valor predeterminado si escribe su propia función de finalización y llama a **set_terminate** con el nombre de la función como su argumento. **Terminate** llama a la última función especificada como argumento para **set_terminate**. Después de realizar las tareas de limpieza deseadas, *termFunction* debe salir del programa. Si no sale (si vuelve a su llamador), se llama a [Abort](abort.md) .

En un entorno multiproceso, las funciones de finalización se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de finalización. Por lo tanto, cada subproceso se encarga de su propio control de finalización.

El tipo **terminate_function** se define en EH. H como puntero a una función de finalización definida por el usuario, *termFunction* que devuelve **void**. La función personalizada *termFunction* no puede tomar ningún argumento y no debe volver a su llamador. Si es así, se llama a [Abort](abort.md) . Una excepción no se puede iniciar desde dentro de *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> La función **set_terminate** solo funciona fuera del depurador.

Hay un único controlador de **set_terminate** para todos los archivos dll o exe vinculados dinámicamente. Aunque llame a **set_terminate** , es posible que el controlador se reemplace por otro, o puede que esté reemplazando un controlador establecido por otro archivo dll o exe.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [terminate](terminate-crt.md).

## <a name="see-also"></a>Vea también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
