---
title: _open_osfhandle
ms.date: 05/21/2019
api_name:
- _open_osfhandle
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
ms.openlocfilehash: 2fa2d8190082967d14dd780aa9be7286996b1f9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951220"
---
# <a name="_open_osfhandle"></a>_open_osfhandle

Asocia un descriptor de archivo en tiempo de ejecución de C a un identificador de archivo del sistema operativo existente.

## <a name="syntax"></a>Sintaxis

```cpp
int _open_osfhandle (
   intptr_t osfhandle,
   int flags
);
```

### <a name="parameters"></a>Parámetros

*osfhandle*<br/>
Identificador de archivo del sistema operativo.

*flags*<br/>
Tipos de operaciones permitidas.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **_open_osfhandle** devuelve un descriptor de archivo en tiempo de ejecución de C. De lo contrario, devuelve -1.

## <a name="remarks"></a>Comentarios

La función **_open_osfhandle** asigna un descriptor de archivo en tiempo de ejecución de C. Asocia este descriptor de archivo con el identificador de archivo del sistema operativo especificado por *osfhandle*. Para evitar una advertencia del compilador, convierta el argumento *osfhandle* de **HANDLE** a **intptr_t**. El argumento *flags* es una expresión de entero formada por una o varias de las constantes del manifiesto, definidas en \<fcntl.h>. Puede usar el operador OR bit a bit ( **&#124;** ) para combinar dos o más constantes de manifiesto para formar el argumento *Flags* .

Estas constantes de manifiesto se definen en \<fcntl.h>:

|||
|-|-|
| **\_O\_APPEND** | Coloca un puntero de archivo al final del archivo antes de cada operación de escritura. |
| **\_O\_RDONLY** | Abre el archivo únicamente para leerlo. |
| **\_O\_TEXT** | Abre el archivo en modo de texto (traducido). |
| **\_O\_WTEXT** | Abre el archivo en modo Unicode (UTF-16 traducido). |

Con la llamada **_open_osfhandle**, se transfiere la propiedad del identificador de archivos de Win32 al descriptor del archivo. Para cerrar un archivo abierto mediante **_open_osfhandle**, llame a [\_close](close.md). El identificador de archivos del sistema operativo subyacente también se cierra mediante una llamada a **_close**. No llame a la función de Win32 **CloseHandle** en el identificador original. Si el descriptor de archivo es propiedad de una secuencia de **archivos &#42;**  , una llamada a [fclose](fclose-fcloseall.md) cierra el descriptor de archivo y el identificador subyacente. En este caso, no llame a **_close** en el descriptor del archivo o a **CloseHandle** en el identificador original.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[\_get_osfhandle](get-osfhandle.md)
