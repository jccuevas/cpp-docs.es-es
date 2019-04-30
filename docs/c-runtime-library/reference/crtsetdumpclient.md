---
title: _CrtSetDumpClient
ms.date: 11/04/2016
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
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: 09f319f6298dbec6b229b2923bd86fc9b50314de
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342994"
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

El **_CrtSetDumpClient** función permite que la aplicación enlace su propia función para volcar objetos almacenados en **_CLIENT_BLOCK** bloques de memoria en el tiempo de ejecución de C depuración el proceso de volcado de memoria. Como resultado, cada vez que una depuración de volcado función como [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) o [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) vuelca un **_CLIENT_BLOCK** bloque de memoria, la aplicación También se llama función de volcado de memoria. **_CrtSetDumpClient** proporciona una aplicación con un método sencillo para detectar pérdidas de memoria y validar o notificar el contenido de los datos almacenados en **_CLIENT_BLOCK** bloques. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtSetDumpClient** se quitan durante el preprocesamiento.

El **_CrtSetDumpClient** función instala la nueva función de volcado de memoria definido por la aplicación especificada en *dumpClient* y devuelve la función de volcado definida previamente. Ejemplo de una función de volcado de bloque de cliente:

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

El *userPortion* argumento es un puntero al principio de la parte de datos de usuario del bloque de memoria y *blockSize* especifica el tamaño de la memoria asignada bloque en bytes. Debe devolver la función de volcado de bloque cliente **void**. El puntero a la función de volcado de memoria de cliente que se pasa a **_CrtSetDumpClient** es de tipo **_CRT_DUMP_CLIENT**, tal como se define en Crtdbg.h:

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Para obtener más información acerca de las funciones que operan en **_CLIENT_BLOCK** bloques de memoria, vea [funciones de enlace de bloque cliente](/visualstudio/debugger/client-block-hook-functions). La función [_CrtReportBlockType](crtreportblocktype.md) se puede usar para devolver información sobre los tipos y subtipos de bloques.

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
