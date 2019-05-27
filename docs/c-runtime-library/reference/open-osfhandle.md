---
title: _open_osfhandle
ms.date: 05/21/2019
apiname:
- _open_osfhandle
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
ms.openlocfilehash: 8527dade37f20b7341d5a26f5752ece668ab7fc9
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174795"
---
# <a name="openosfhandle"></a>_open_osfhandle

Asocia un descriptor de archivo en tiempo de ejecución de C al identificador de archivo del sistema operativo existente.

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

La función **_open_osfhandle** asigna un descriptor de archivo en tiempo de ejecución de C y lo asocia al identificador de archivo del sistema operativo especificado por *osfhandle*. Para evitar una advertencia del compilador, convierta el argumento *osfhandle* de **HANDLE** a **intptr_t**. El argumento *flags* es una expresión de entero formada por una o varias de las constantes del manifiesto, definidas en \<fcntl.h>. Cuando se usan dos o más constantes del manifiesto para formar el argumento *flags*, estas constantes se combinan con el operador bit a bit OR (**&#124;**).

Estas constantes de manifiesto se definen en \<fcntl.h>:

|||
|-|-|
| **\_O\_APPEND** | Coloca un puntero de archivo al final del archivo antes de cada operación de escritura. |
| **\_O\_RDONLY** | Abre el archivo únicamente para leerlo. |
| **\_O\_TEXT** | Abre el archivo en modo de texto (traducido). |
| **\_O\_WTEXT** | Abre el archivo en modo Unicode (UTF-16 traducido). |

Con la llamada **_open_osfhandle**, se transfiere la propiedad del identificador de archivos de Win32 al descriptor del archivo. Para cerrar un archivo abierto mediante **_open_osfhandle**, llame a [\_close](close.md). El identificador de archivos del sistema operativo subyacente también se cierra mediante una llamada a **_close**. No llame a la función de Win32 **CloseHandle** en el identificador original. Si el descriptor del archivo pertenece a un flujo **FILE &#42;**, el hecho de llamar a [fclose](fclose-fcloseall.md) en dicho flujo **FILE &#42;** cerrará tanto el descriptor del archivo como el identificador subyacente. En este caso, no llame a **_close** en el descriptor del archivo o a **CloseHandle** en el identificador original.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
