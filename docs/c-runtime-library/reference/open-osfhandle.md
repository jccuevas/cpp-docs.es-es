---
title: _open_osfhandle
ms.date: 4/2/2020
api_name:
- _open_osfhandle
- _o__open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 16966bedd80dc90eaa89ee46e6b633a9cf7af74f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338543"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

Asocia un descriptor de archivo en tiempo de ejecución de C con un identificador de archivo de sistema operativo existente.

## <a name="syntax"></a>Sintaxis

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Parámetros

*osfhandle*<br/>
Mango de archivo del sistema operativo.

*Banderas*<br/>
Tipos de operaciones permitidas.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **_open_osfhandle** devuelve un descriptor de archivo en tiempo de ejecución de C. De lo contrario, devuelve -1.

## <a name="remarks"></a>Observaciones

La función **_open_osfhandle** asigna un descriptor de archivo en tiempo de ejecución de C. Asocia este descriptor de archivo con el identificador de archivo del sistema operativo especificado por *osfhandle*. Para evitar una advertencia del compilador, convierta el argumento *osfhandle* de **HANDLE** a **intptr_t**. El argumento *flags* es una expresión de entero formada por una o varias de las constantes del manifiesto, definidas en \<fcntl.h>. Puede utilizar el operador OR bit a bit ( **&#124;** ) para combinar dos o más constantes de manifiesto para formar el argumento *flags.*

Estas constantes de manifiesto se definen en \<fcntl.h>:

|||
|-|-|
| **\_O\_APPEND** | Coloca un puntero de archivo al final del archivo antes de cada operación de escritura. |
| **\_O\_RDONLY** | Abre el archivo únicamente para leerlo. |
| **\_O\_TEXTO** | Abre el archivo en modo de texto (traducido). |
| **\_O\_WTEXT** | Abre el archivo en modo Unicode (UTF-16 traducido). |

Con la llamada **_open_osfhandle**, se transfiere la propiedad del identificador de archivos de Win32 al descriptor del archivo. Para cerrar un archivo abierto mediante **_open_osfhandle**, llame a [\_close](close.md). El identificador de archivos del sistema operativo subyacente también se cierra mediante una llamada a **_close**. No llame a la función de Win32 **CloseHandle** en el identificador original. Si el descriptor de archivo es propiedad de una secuencia **de &#42;de archivo,** una llamada a [fclose](fclose-fcloseall.md) cierra el descriptor de archivo y el identificador subyacente. En este caso, no llame a **_close** en el descriptor del archivo o a **CloseHandle** en el identificador original.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
