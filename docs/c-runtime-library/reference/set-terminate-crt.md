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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 08ea5bb8c446fadac6a7bcf7ca172c5d14546776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332102"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Instala su propia rutina de terminación para ser llamada por **terminate**.

## <a name="syntax"></a>Sintaxis

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parámetros

*termFunction*<br/>
Puntero a una función de finalización que se escribe.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función anterior registrada por **set_terminate** para que la función anterior se pueda restaurar más adelante. Si no se ha establecido ninguna función anterior, se puede utilizar el valor devuelto para restaurar el comportamiento predeterminado; este valor puede ser **NULL**.

## <a name="remarks"></a>Observaciones

La función **set_terminate** instala *termFunction* como la función a la que llama **terminate**. **set_terminate** se utiliza con el control de excepciones De C++ y se puede llamar en cualquier momento del programa antes de que se produzca la excepción. **terminar** las llamadas [abortan de](abort.md) forma predeterminada. Puede cambiar este valor predeterminado escribiendo su propia función de terminación y llamando a **set_terminate** con el nombre de la función como argumento. **terminate** llama a la última función dada como argumento para **set_terminate**. Después de realizar las tareas de limpieza deseadas, *termFunction* debe salir del programa. Si no se cierra (si vuelve a su llamador), se llama a [abort.](abort.md)

En un entorno multiproceso, las funciones de finalización se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de finalización. Por lo tanto, cada subproceso se encarga de su propio control de finalización.

El tipo **terminate_function** se define en EH. H como puntero a una función de terminación definida por el usuario, *termFunction* que devuelve **void**. La función personalizada *termFunction* no puede tomar ningún argumento y no debe volver a su llamador. Si lo hace, se llama [a abortar.](abort.md) No se puede producir una excepción desde dentro de *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> La función **set_terminate** solo funciona fuera del depurador.

Hay un único controlador **de set_terminate** para todos los archivos DLL o EXE vinculados dinámicamente; incluso si llama a **set_terminate** el controlador puede reemplazarse por otro, o puede reemplazar un controlador establecido por otro archivo DLL o EXE.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [terminate](terminate-crt.md).

## <a name="see-also"></a>Consulte también

[Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)<br/>
[Aborta](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Terminar](terminate-crt.md)<br/>
[Inesperado](unexpected-crt.md)<br/>
