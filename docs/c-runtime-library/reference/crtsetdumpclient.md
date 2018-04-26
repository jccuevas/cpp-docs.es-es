---
title: _CrtSetDumpClient | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6682c74ca81628efd17a654cc6d810e516e807b2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient

Instala una función definida por la aplicación para volcar **_CLIENT_BLOCK** escriba bloques de memoria (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>Parámetros

*dumpClient*<br/>
Nueva función de volcado de memoria definida por el cliente que se va a enlazar al proceso de volcado de memoria de depuración en tiempo de ejecución de C.

## <a name="return-value"></a>Valor devuelto

Devuelve la función previamente definida de volcado de bloques de cliente.

## <a name="remarks"></a>Comentarios

El **_CrtSetDumpClient** función permite que la aplicación enlace su propia función para volcar objetos almacenados en **_CLIENT_BLOCK** proceso de volcado de memoria de depuración de bloques de memoria en el tiempo de ejecución de C. Como resultado, cada vez que una depuración de volcado de memoria función como [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) o [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) vuelca un **_CLIENT_BLOCK** bloque de memoria, la aplicación se llama también a la función de volcado de memoria. **_CrtSetDumpClient** proporciona una aplicación con un método sencillo para detectar pérdidas de memoria y validar o notificar el contenido de los datos almacenados en **_CLIENT_BLOCK** bloques. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtSetDumpClient** se quitan durante el preprocesamiento.

El **_CrtSetDumpClient** función instala la nueva función de volcado definida por la aplicación especificada en *dumpClient* y devuelve la función de volcado definida previamente. Ejemplo de una función de volcado de bloque de cliente:

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

El *userPortion* argumento es un puntero al principio de la parte de datos de usuario del bloque de memoria y *blockSize* especifica el tamaño de la memoria asignada bloque en bytes. La función de volcado de memoria de bloque de cliente debe devolver **void**. El puntero a la función de volcado de memoria de cliente que se pasa a **_CrtSetDumpClient** es de tipo **_CRT_DUMP_CLIENT**, tal como se define en Crtdbg.h:

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Para obtener más información acerca de las funciones que operan en **_CLIENT_BLOCK** tipos de bloques de memoria, vea [funciones de enlace de bloque cliente](/visualstudio/debugger/client-block-hook-functions). La función [_CrtReportBlockType](crtreportblocktype.md) se puede usar para devolver información sobre los tipos y subtipos de bloques.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
