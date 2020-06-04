---
title: set_terminate (CRT)
ms.date: 4/2/2020
api_name:
- set_terminate
- _o_set_terminate
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 29b760d8831411142aad052fdef510efb0486747
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914516"
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

## <a name="remarks"></a>Observaciones

La función **set_terminate** instala *termFunction* como la función a la que llama **Terminate**. **set_terminate** se usa con el control de excepciones de C++ y se puede llamar en cualquier punto del programa antes de que se produzca la excepción. la instrucción **Terminate** llama a [Abort](abort.md) de forma predeterminada. Puede cambiar este valor predeterminado si escribe su propia función de finalización y llama a **set_terminate** con el nombre de la función como su argumento. **Terminate** llama a la última función especificada como argumento para **set_terminate**. Después de realizar las tareas de limpieza deseadas, *termFunction* debe salir del programa. Si no sale (si vuelve a su llamador), se llama a [Abort](abort.md) .

En un entorno multiproceso, las funciones de finalización se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de finalización. Por lo tanto, cada subproceso se encarga de su propio control de finalización.

El tipo de **terminate_function** se define en EH. H como puntero a una función de finalización definida por el usuario, *termFunction* que devuelve **void**. La función personalizada *termFunction* no puede tomar ningún argumento y no debe volver a su llamador. Si es así, se llama a [Abort](abort.md) . Una excepción no se puede iniciar desde dentro de *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> La función **set_terminate** solo funciona fuera del depurador.

Hay un único controlador de **set_terminate** para todos los archivos dll o exe vinculados dinámicamente. incluso si llama a **set_terminate** el controlador puede reemplazarse por otro, o puede que esté reemplazando un controlador establecido por otro archivo dll o exe.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [terminate](terminate-crt.md).

## <a name="see-also"></a>Consulta también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[aborta](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[cancela](terminate-crt.md)<br/>
[esperado](unexpected-crt.md)<br/>
