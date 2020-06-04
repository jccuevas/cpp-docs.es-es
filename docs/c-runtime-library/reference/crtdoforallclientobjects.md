---
title: _CrtDoForAllClientObjects
ms.date: 11/04/2016
api_name:
- _CrtDoForAllClientObjects
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
ms.openlocfilehash: 4626df0db1956efd26ee267cb8cacf8ea4a4570c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942530"
---
# <a name="_crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Llama a una función proporcionada por la aplicación para todos los tipos _ **client_block** del montón (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Parámetros

*pfn*<br/>
Puntero a la función de devolución de llamada proporcionada por la aplicación. El primer parámetro de esta función señala a los datos. El segundo parámetro es el puntero de contexto que se pasa a la llamada a _ **crtdoforallclientobjects**.

*context*<br/>
Puntero al contexto proporcionado por la aplicación que se va a pasar a la función proporcionada por la aplicación.

## <a name="remarks"></a>Comentarios

La función _ **crtdoforallclientobjects** busca en la lista vinculada del montón bloques de memoria con el tipo _ **client_block** y llama a la función proporcionada por la aplicación cuando se encuentra un bloque de este tipo. El bloque encontrado y el parámetro de *contexto* se pasan como argumentos a la función proporcionada por la aplicación. Durante la depuración, una aplicación puede realizar el seguimiento de un grupo específico de asignaciones llamando explícitamente a las funciones del montón de depuración para asignar la memoria y especificando que se asigna a los bloques el tipo de bloque _ **client_block** . A continuación, se puede realizar el seguimiento y la notificación de estos bloques por separado durante la detección de pérdidas y la creación de informes sobre el estado de la memoria.

Si el campo de bits **_CRTDBG_ALLOC_MEM_DF** de la marca _ [crtdbgflag](../../c-runtime-library/crtdbgflag.md) no está activado, _ **crtdoforallclientobjects** devuelve inmediatamente. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a _ **crtdoforallclientobjects** se quitan durante el preprocesamiento.

Para obtener más información sobre el tipo _ **client_block** y cómo lo pueden usar otras funciones de depuración, vea [tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Si *pfn* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establecen en **EINVAL** y la función devuelve.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Libre** Solo las versiones de depuración de las bibliotecas en tiempo de ejecución de C universales.

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
