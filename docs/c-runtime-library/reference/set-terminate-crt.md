---
title: set_terminate (CRT)
ms.date: 11/04/2016
apiname:
- set_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 7be81dec7fba80a273d635cbd30b96b09928bc66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356451"
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

Instala su propia rutina de finalización para ser llamado por **finalizar**.

## <a name="syntax"></a>Sintaxis

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parámetros

*termFunction*<br/>
Puntero a una función de finalización que se escribe.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función anterior registrada por **set_terminate** para que la función anterior se puede restaurar más adelante. Si no se ha establecido ninguna función anterior, el valor devuelto puede utilizarse para restaurar el comportamiento predeterminado; Este valor puede ser **NULL**.

## <a name="remarks"></a>Comentarios

El **set_terminate** función instalaciones *termFunction* como la función llamada por **finalizar**. **set_terminate** se usa con C++ control de excepciones y se puede llamar en cualquier momento en el programa antes de que se produce la excepción. **Finalizar** llamadas [anular](abort.md) de forma predeterminada. Puede cambiar este comportamiento predeterminado escribiendo su propia función de finalización y llamar a **set_terminate** con el nombre de la función como su argumento. **Finalizar** llama a la última función especificada como argumento a **set_terminate**. Después de llevar a cabo cualquier tarea de limpieza, de deseada *termFunction* debe salir del programa. Si no existe (si se devuelve a su llamador), [anular](abort.md) se llama.

En un entorno multiproceso, las funciones de finalización se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de finalización. Por lo tanto, cada subproceso se encarga de su propio control de finalización.

El **terminate_function** tipo está definido en el controlador de eventos. H como un puntero a una función de finalización definida por el usuario, *termFunction* que devuelve **void**. La función personalizada *termFunction* puede tomar ningún argumento y no debe devolver al llamador. Si es así, [anular](abort.md) se llama. No se puede producir una excepción desde *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> El **set_terminate** función solo funciona fuera del depurador.

Solo hay un **set_terminate** controlador para todos los dinámicamente exe y DLL vinculados; incluso si se llama a **set_terminate** el controlador puede reemplazarse por otro, o que puede sustituir un controlador establecido por otro Archivo DLL o EXE.

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
