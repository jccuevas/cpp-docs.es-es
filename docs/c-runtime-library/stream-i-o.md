---
title: E/S de secuencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3fba53f16fad9321701e641020ed01349b13a5c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418112"
---
# <a name="stream-io"></a>E/S de secuencia

Estas funciones procesan datos de diferentes tamaños y formatos, desde caracteres individuales a estructuras de datos de gran tamaño. También proporcionan almacenamiento en búfer, que puede mejorar el rendimiento. El tamaño predeterminado de un búfer de secuencia es 4K. Estas rutinas afectan sólo a los búferes creados por las rutinas de biblioteca en tiempo de ejecución y no tienen ningún efecto en los búferes creados por el sistema operativo.

## <a name="stream-io-routines"></a>Rutinas de E/S de secuencia

|Rutina|Usar|
|-------------|---------|
|[clearerr](../c-runtime-library/reference/clearerr.md), [clearerr_s](../c-runtime-library/reference/clearerr-s.md)|Indicador de borrar error para la secuencia|
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|Cerrar secuencia|
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|Cerrar todas las secuencias abiertas excepto **stdin**, **stdout** y **stderr**|
|[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Asociar la secuencia con un descriptor de archivo del archivo abierto|
|[feof](../c-runtime-library/reference/feof.md)|Prueba de fin de archivo en secuencia|
|[ferror](../c-runtime-library/reference/ferror.md)|Prueba de error en secuencia|
|[fflush](../c-runtime-library/reference/fflush.md)|Vaciar la secuencia en el búfer o en el dispositivo de almacenamiento|
|[fgetc, fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|Leer carácter de la secuencia (versiones de función de **getc** y **getwc**)|
|[_fgetchar, _fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|Leer carácter de **stdin** (versiones de función de **getchar** y **getwchar**)|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|Obtener el indicador de posición de la secuencia|
|[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)|Leer cadena de la secuencia|
|[_fileno](../c-runtime-library/reference/fileno.md)|Obtener el descriptor de archivo asociado con la secuencia|
|[_flushall](../c-runtime-library/reference/flushall.md)|Vaciar todas las secuencias en el búfer o en el dispositivo de almacenamiento|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Abrir secuencia|
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|Escribe datos con formato en la secuencia|
|[fputc, fputwc](../c-runtime-library/reference/fputc-fputwc.md)|Escribir un carácter en una secuencia (versiones de función de **putc** y **putwc**)|
|[_fputchar, _fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|Escribir carácter en **stdout** (versiones de función de **putchar** y **putwchar**)|
|[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)|Escribir cadena en la secuencia|
|[fread](../c-runtime-library/reference/fread.md)|Leer datos sin formato de la secuencia|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Reasignar el puntero de la secuencia **FILE** al nuevo archivo o dispositivo|
|[fscanf, fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|Leer datos con formato de la secuencia|
|[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|Mover posición de archivo a la ubicación dada|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|Establecer el indicador de posición de la secuencia|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Abre una secuencia con uso compartido de archivos.|
|[ftell, _ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|Obtener la posición del archivo actual|
|[fwrite](../c-runtime-library/reference/fwrite.md)|Escribir elementos de datos sin formato en la secuencia|
|[getc, getwc](../c-runtime-library/reference/getc-getwc.md)|Leer carácter de la secuencia (versiones de macro de **fgetc** y **fgetwc**)|
|[getchar, getwchar](../c-runtime-library/reference/getc-getwc.md)|Leer carácter de **stdin** (versiones de macro de **fgetchar** y **fgetwchar**)|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|Devuelve el número de archivos que se permite abrir simultáneamente en el nivel de E/S de secuencia.|
|[gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|Leer línea de **stdin**|
|[_getw](../c-runtime-library/reference/getw.md)|Leer **int** binario de la secuencia|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Escribir datos con formato en **stdout**|
|[putc, putwc](../c-runtime-library/reference/putc-putwc.md)|Escribir carácter en una secuencia (versiones de macro de **fputc** y **fputwc**)|
|[putchar, putwchar](../c-runtime-library/reference/putc-putwc.md)|Escribir carácter en **stdout** (versiones de macro de **fputchar** y **fputwchar**)|
|[puts, _putws](../c-runtime-library/reference/puts-putws.md)|Escribir línea en la secuencia|
|[_putw](../c-runtime-library/reference/putw.md)|Escribir **int** binario en la secuencia|
|[rewind](../c-runtime-library/reference/rewind.md)|Mover la posición de archivo al principio de la secuencia|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|Quitar archivos temporales creados por **tmpfile**|
|[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Leer datos con formato de **stdin**|
|[setbuf](../c-runtime-library/reference/setbuf.md)|Controlar el almacenamiento en búfer de la secuencia|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|Establece el número de archivos que se permite abrir simultáneamente en el nivel de E/S de secuencia.|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|Controlar el almacenamiento en búfer de la secuencia y el tamaño del búfer|
|[_snprintf, _snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|Escribir datos con formato de la longitud especificada en la cadena|
|[_snscanf, _snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md), [_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|Lee los datos con formato de una longitud especificada del flujo de entrada estándar.|
|[sprintf, swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Escribir datos con formato en cadena|
|[sscanf, swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md), [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Leer datos con formato de la cadena|
|[_tempnam, _wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|Generar un nombre de archivo temporal en el directorio dado|
|[tmpfile](../c-runtime-library/reference/tmpfile.md), [tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|Crear un archivo temporal|
|[tmpnam, _wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md), [tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|Generar un nombre de archivo temporal|
|[ungetc, ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|Insertar el carácter de nuevo en la secuencia|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md), [_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|Escribir datos con formato en la consola.|
|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|Escribe datos con formato en la secuencia|
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), [vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|Escribir datos con formato en **stdout**|
|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md), [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Escribir datos con formato de la longitud especificada en el búfer|
|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md), [vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|Escribir datos con formato en el búfer|

 Cuando un programa inicia la ejecución, el código de inicio abre automáticamente varias secuencias: entrada estándar (señalada por **stdin**), salida estándar (señalada por **stdout**) y errores estándar (señalada por **stderr**). Estas secuencias se dirigen a la consola (teclado y pantalla) de forma predeterminada. Use **freopen** para redirigir **stdin**, **stdout** o **stderr** a un archivo de disco o un dispositivo.

 Los archivos abiertos con las rutinas de secuencia se almacenan en búfer de forma predeterminada. Las funciones **stdout** y **stderr** se vacían siempre que están llenas o, si está escribiendo en un dispositivo de caracteres, tras cada llamada a la biblioteca. Si un programa finaliza incorrectamente, los búferes de salida pueden no ser vaciados, lo que resulta en pérdida de datos. Use **fflush** o **_flushall** para asegurarse de que el búfer asociado con un archivo especificado o todos los búferes abiertos se vacían en el sistema operativo, que puede almacenar datos en caché antes de escribir en el disco. La característica de confirmación en disco garantiza que el contenido del búfer de vaciado no se pierda si se produce un error del sistema.

 Hay dos formas de confirmar el contenido del búfer en el disco:

-   Vincular con el archivo COMMODE.OBJ para establecer una un indicador global de confirmación. El valor predeterminado del indicador global es **n** para "no-commit".

-   Defina el indicador de modo en **c** con **fopen** o **_fdopen**.

 Cualquier archivo que se abra específicamente con el indicador **c** o **n** se comporta según el indicador, independientemente del estado del indicador global commit/no-commit.

 Si el programa no cierra explícitamente una secuencia, la secuencia se cierra automáticamente cuando finaliza el programa. Sin embargo, debe cerrar una secuencia cuando el programa termina de usarla, ya que el número de secuencias que pueden estar abiertas al mismo tiempo es limitado. Vea [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) para obtener información sobre este límite.

 La entrada puede seguir directamente a la salida solo con una llamada intermedia a **fflush** o a una función de posicionamiento de archivo (**fseek**, **fsetpos** o **rewind**). La salida puede seguir a la entrada sin una llamada intermedia a una función de posicionamiento de archivo si la operación de entrada encuentra el final del archivo.

## <a name="see-also"></a>Vea también

[Entrada y salida](../c-runtime-library/input-and-output.md)<br/>
 [Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
