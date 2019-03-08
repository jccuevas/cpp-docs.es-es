---
title: _open_osfhandle
ms.date: 05/29/2018
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
ms.openlocfilehash: f45ca46cae459c8606f88a98d03b64c40e5d5f01
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327868"
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

Si es correcto, **_open_osfhandle** devuelve un descriptor de archivo de tiempo de ejecución de C. En caso contrario, devuelve -1.

## <a name="remarks"></a>Comentarios

El **_open_osfhandle** función asigna un descriptor de archivo de tiempo de ejecución de C y lo asocia con el identificador de archivo del sistema operativo especificado por *osfhandle*. Para evitar una advertencia del compilador, convierta el *osfhandle* argumento desde **controlar** a **intptr_t**. El *marcas* argumento es una expresión de entero formada a partir de uno o más constantes del manifiesto definidos en \<fcntl.h >. Cuando se usan dos o más constantes de manifiesto para formar el *marcas* argumento, estas constantes se combinan con el operador OR bit a bit ( **&#124;** ).

Estas constantes de manifiesto se definen en \<fcntl.h >:

|||
|-|-|
| **\_O\_APPEND** | Coloca un puntero de archivo al final del archivo antes de cada operación de escritura. |
| **\_O\_RDONLY** | Abre el archivo únicamente para leerlo. |
| **\_O\_TEXTO** | Abre el archivo en modo de texto (traducido). |
| **\_O\_WTEXT** | Abre el archivo en modo Unicode (UTF-16 traducido). |

El **_open_osfhandle** llamada transfiere la propiedad del identificador de archivo de Win32 en el descriptor de archivo. Para cerrar un archivo abierto con **_open_osfhandle**, llame a [ \_cerrar](close.md). También se cierra el identificador de archivo del sistema operativo subyacente mediante una llamada a **_close**, por lo que no es necesario llamar a la función de Win32 **CloseHandle** en el identificador original. Si el descriptor de archivo pertenece a un **archivo &#42;**  secuencia, a continuación, llamar a [fclose](fclose-fcloseall.md) en que **archivo &#42;**  secuencia también tanto el descriptor de archivo cierra y el identificador subyacente. En este caso, no llame a **_close** en el descriptor de archivo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_open_osfhandle**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
