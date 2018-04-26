---
title: _CrtDoForAllClientObjects | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtDoForAllClientObjects
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
- _CrtDoForAllClientObjects
- CrtDoForAllClientObjects
- crtdbg/_CrdDoForAllClientObjects
dev_langs:
- C++
helpviewer_keywords:
- _CrtDoForAllClientObjects function
- CrtDoForAllClientObjects function
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 83c555899807c9236b803b0576bc8bf6884fd944
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="crtdoforallclientobjects"></a>_CrtDoForAllClientObjects

Llama a una función proporcionada por la aplicación para todos los **_CLIENT_BLOCK** tipos en el montón (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtDoForAllClientObjects(
   void ( * pfn )( void *, void * ),
   void *context
);
```

### <a name="parameters"></a>Parámetros

*PFN* puntero a la función de devolución de llamada de función proporcionada por la aplicación. El primer parámetro de esta función señala a los datos. El segundo parámetro es el puntero de contexto que se pasa a la llamada a **_CrtDoForAllClientObjects**.

*contexto* puntero al contexto proporcionada por la aplicación para pasar a la función proporcionada por la aplicación.

## <a name="remarks"></a>Comentarios

El **_CrtDoForAllClientObjects** función busca en la lista del montón vinculado bloques de memoria con el **_CLIENT_BLOCK** tipo y llama a la función proporcionada por la aplicación cuando un bloque de este tipo se encuentra. El bloque encontrado y el *contexto* parámetro se pasan como argumentos a la función proporcionada por la aplicación. Durante la depuración, una aplicación puede realizar un seguimiento de un grupo específico de asignaciones llamando explícitamente a la depuración funciones del montón para asignar memoria y especificando que se asigne a los bloques de la **_CLIENT_BLOCK** tipo de bloque. A continuación, se puede realizar el seguimiento y la notificación de estos bloques por separado durante la detección de pérdidas y la creación de informes sobre el estado de la memoria.

Si el **_CRTDBG_ALLOC_MEM_DF** campo de bits de la [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) marca no está activada, **_CrtDoForAllClientObjects** devuelve inmediatamente. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtDoForAllClientObjects** se quitan durante el preprocesamiento.

Para obtener más información sobre la **_CLIENT_BLOCK** escribir y ver cómo puede usar otras funciones de depuración, [tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Si *pfn* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) está establecido en **EINVAL** y devuelve la función.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtDoForAllClientObjects**|\<crtdbg.h>, \<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Bibliotecas:** solo versiones de depuración de las bibliotecas en tiempo de ejecución de C universales.

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
[Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
