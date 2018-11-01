---
title: _set_new_handler
ms.date: 11/04/2016
apiname:
- _set_new_handler
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
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: bc7718503f59c69868a75cac9383286a548fc307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640315"
---
# <a name="setnewhandler"></a>_set_new_handler

Transfiere el control al mecanismo de control de errores si el operador **new** no puede asignar memoria.

## <a name="syntax"></a>Sintaxis

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Parámetros

*pNewHandler*<br/>
Puntero a la función de control de memoria proporcionada por la aplicación. Un argumento de 0 hace que se quite el nuevo controlador.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la función registrada por de control de excepciones anterior **_set_new_handler**, de modo que la función anterior se puede restaurar más adelante. Si no se ha establecido ninguna función anterior, el valor devuelto puede utilizarse para restaurar el comportamiento predeterminado; Este valor puede ser **NULL**.

## <a name="remarks"></a>Comentarios

El C++ **_set_new_handler** función especifica una función de control de excepciones que obtiene el control si el **nuevo** operador no puede asignar memoria. Si **nueva** se produce un error, el sistema de tiempo de ejecución llama automáticamente a la función de control de excepciones que se pasó como argumento a **_set_new_handler**. **_PNH**, definido en New.h, es un puntero a una función que devuelve el tipo **int** y toma un argumento de tipo **size_t**. Use **size_t** para especificar la cantidad de espacio que se va a asignar.

No hay ningún controlador predeterminado.

**_set_new_handler** es básicamente un esquema de la colección de elementos no utilizados. El sistema de tiempo de ejecución reintenta la asignación cada vez que la función devuelve un valor distinto de cero y se produce un error si la función devuelve 0.

Una repetición de la **_set_new_handler** función en un programa registra la función de control de excepciones especificada en la lista de argumentos con el sistema de tiempo de ejecución:

```cpp
// set_new_handler1.cpp
#include <new.h>

int handle_program_memory_depletion( size_t )
{
   // Your code
}

int main( void )
{
   _set_new_handler( handle_program_memory_depletion );
   int *pi = new int[BIG_NUMBER];
}
```

Puede guardar la dirección de la función que se pasó por última vez a la **_set_new_handler** de función y restablecerla más adelante:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

La función [_set_new_mode](set-new-mode.md) de C++ establece el nuevo modo de controlador para [malloc](malloc.md). El nuevo modo de controlador indica si, en caso de error, **malloc** consiste en llamar a la rutina del nuevo controlador según lo establecido por **_set_new_handler**. De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error para asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **malloc** no puede asignar memoria, **malloc** llame a la rutina del nuevo controlador de la misma forma en que el **nuevo** operador Cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a:

```cpp
_set_new_mode(1);
```

temprano en el programa o vincúlelo con Newmode.obj.

Si un usuario definido por el `operator new` es siempre, las nuevas funciones de controlador no se llaman automáticamente en caso de error.

Para obtener más información, vea los operadores [new](../../cpp/new-operator-cpp.md) y [delete](../../cpp/delete-operator-cpp.md) en *Referencia de lenguaje C++*.

Solo hay un **_set_new_handler** controlador para dinámicamente todos los ejecutables y DLL vinculados; incluso si se llama a **_set_new_handler** el controlador es posible que se reemplace por otro o que se va a sustituir un controlador establecido por otro ejecutable o DLL.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

En este ejemplo, cuando se produce un error en la asignación, el control se transfiere a MyNewHandler. El argumento pasado a MyNewHandler es el número de bytes solicitados. El valor devuelto de MyNewHandler es una marca que indica si se debe reintentar la asignación: un valor distinto de cero indica que se debe reintentar la asignación, mientras que un valor de cero indica que se ha producido un error en la asignación.

```cpp
// crt_set_new_handler.cpp
// compile with: /c
#include <stdio.h>
#include <new.h>
#define BIG_NUMBER 0x1fffffff

int coalesced = 0;

int CoalesceHeap()
{
   coalesced = 1;  // Flag RecurseAlloc to stop
   // do some work to free memory
   return 0;
}
// Define a function to be called if new fails to allocate memory.
int MyNewHandler( size_t size )
{
   printf("Allocation failed. Coalescing heap.\n");

   // Call a function to recover some heap space.
   return CoalesceHeap();
}

int RecurseAlloc() {
   int *pi = new int[BIG_NUMBER];
   if (!coalesced)
      RecurseAlloc();
   return 0;
}

int main()
{
   // Set the failure handler for new to be MyNewHandler.
   _set_new_handler( MyNewHandler );
   RecurseAlloc();
}
```

```Output
Allocation failed. Coalescing heap.

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
