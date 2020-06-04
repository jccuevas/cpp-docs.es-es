---
title: _CrtSetDumpClient
ms.date: 11/04/2016
api_name:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: f739f86a8410c66135704d61944d122a38c196a5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938571"
---
# <a name="_crtsetdumpclient"></a>_CrtSetDumpClient

Instala una función definida por la aplicación para volcar bloques de memoria de tipo _ **client_block** (solo versión de depuración).

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

La función _ **crtsetdumpclient** permite que la aplicación enlace su propia función para volcar objetos almacenados en bloques de memoria _ **client_block** en el proceso de volcado de memoria de depuración en tiempo de ejecución de C. Como resultado, cada vez que una función de volcado de depuración como [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) o _ [crtdumpmemoryleaks](crtdumpmemoryleaks.md) vuelca un bloque de memoria _ **client_block** , también se llama a la función de volcado de la aplicación. _ **Crtsetdumpclient** proporciona a una aplicación un método sencillo para detectar pérdidas de memoria y validar o notificar el contenido de los datos almacenados en bloques _ **client_block** . Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a _ **crtsetdumpclient** se quitan durante el preprocesamiento.

La función _ **crtsetdumpclient** instala la nueva función de volcado definida por la aplicación especificada en *dumpClient* y devuelve la función de volcado definida previamente. Ejemplo de una función de volcado de bloque de cliente:

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

El argumento *userPortion* es un puntero al principio de la parte de datos del usuario del bloque de memoria y *blocksize* especifica el tamaño del bloque de memoria asignado en bytes. La función de volcado de bloque de cliente debe devolver **void**. El puntero a la función de volcado de cliente que se pasa a _ **crtsetdumpclient** es de tipo **_CRT_DUMP_CLIENT**, tal y como se define en CRTDBG. h:

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Para obtener más información sobre las funciones que operan en bloques de memoria de tipo _ **client_block** , consulte [funciones de enlace de bloque de cliente](/visualstudio/debugger/client-block-hook-functions). La función [_CrtReportBlockType](crtreportblocktype.md) se puede usar para devolver información sobre los tipos y subtipos de bloques.

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
