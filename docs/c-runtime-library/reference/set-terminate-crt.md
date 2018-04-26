---
title: set_terminate (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02c38d8c832c4b84725dc15c280c8b3f3fd27841
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

Devuelve un puntero a la función anterior registrada por **set_terminate** para que la función anterior puede restaurarse más tarde. Si no se ha establecido ninguna función anterior, el valor devuelto se puede usar para restaurar el comportamiento predeterminado; puede que este valor sea NULL.

## <a name="remarks"></a>Comentarios

El **set_terminate** función instala *termFunction* como la función llamada a **finalizar**. **set_terminate** se utiliza con control de excepciones de C++ y se puede llamar en cualquier momento en el programa antes de que se produce la excepción. **terminar** llamadas [anular](abort.md) de forma predeterminada. Puede cambiar este comportamiento predeterminado escribiendo su propia función de finalización y llamando a **set_terminate** con el nombre de la función como su argumento. **terminar** llama a la última función especificada como argumento a **set_terminate**. Después de realizar ninguna deseado tareas de limpieza, *termFunction* debe salir del programa. Si no existe (si vuelve a quien), [anular](abort.md) se llama.

En un entorno multiproceso, las funciones de finalización se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de finalización. Por lo tanto, cada subproceso se encarga de su propio control de finalización.

El **terminate_function** tipo está definido en el controlador de eventos. H como un puntero a una función definida por el usuario de terminación, *termFunction* que devuelve **void**. La función personalizada *termFunction* puede no toman ningún argumento y no debe devolver al llamador. Si es así, [anular](abort.md) se llama. No se puede producir una excepción desde *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> El **set_terminate** función solo funciona fuera del depurador.

Hay una sola **set_terminate** controlador para vinculados dinámicamente todos los archivos DLL o exe; incluso si se llama a **set_terminate** el controlador puede reemplazarse por otro, o que puede sustituir un controlador establecido por otro Archivo DLL o EXE.

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
