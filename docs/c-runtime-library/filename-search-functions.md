---
title: Funciones de búsqueda de nombre de archivo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 777ac61828abbdc93bdf3fe6ceda05f927472494
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391807"
---
# <a name="filename-search-functions"></a>Funciones de búsqueda de nombre de archivo
Estas funciones buscan y cierran búsquedas de los nombres de archivos especificados:  
  
-   [_findnext, _wfindnext](../c-runtime-library/reference/findnext-functions.md)  
  
-   [_findfirst, _wfindfirst](../c-runtime-library/reference/findfirst-functions.md)  
  
-   [_findclose](../c-runtime-library/reference/findclose.md)  
  
## <a name="remarks"></a>Comentarios  
 La función `_findfirst` proporciona información acerca de la primera instancia de un nombre de archivo que coincide con el archivo especificado en el argumento `filespec` . En `filespec` , puede usar cualquier combinación de caracteres comodín que sea compatible con el sistema operativo host.  
  
 Las funciones devuelven la información del archivo en una estructura `_finddata_t` , que se define en IO.h. Varias funciones de la familia usan diferentes variaciones en la estructura `_finddata_t` . La estructura `_finddata_t` básica incluye los siguientes elementos:  
  
 `unsigned attrib`  
 Atributo de archivo.  
  
 `time_t time_create`  
 Hora de creación del archivo (-1L para sistemas de archivos FAT). Esta hora se almacena en formato UTC. Para convertir a la hora local, use [localtime_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).  
  
 `time_t time_access`  
 Hora de último acceso al archivo (-1L para sistemas de archivos FAT). Esta hora se almacena en formato UTC. Para convertir a la hora local, use `localtime_s`.  
  
 `time_t time_write`  
 Hora de la última escritura en el archivo. Esta hora se almacena en formato UTC. Para convertir a la hora local, use `localtime_s`.  
  
 `_fsize_t size`  
 Longitud del archivo en bytes.  
  
 `char name`[ `_MAX_PATH`]  
 Nombre terminado en null del archivo o directorio coincidente, sin la ruta de acceso.  
  
 En los sistemas de archivos que no admiten las horas de creación y últimos accesos a un archivo, como el sistema FAT, los campos `time_create` y `time_access` siempre son -1L.  
  
 `_MAX_PATH` se define en Stdlib.h como 260 bytes.  
  
 No puede especificar atributos de destino (como `_A_RDONLY`) para limitar la operación de búsqueda. Estos atributos se devuelven en el campo `attrib` de la estructura `_finddata_t` y puede tener los valores siguientes (definidos en IO.h). Los usuarios no deben depender de que estos sean los únicos valores posibles para el campo `attrib` .  
  
 `_A_ARCH`  
 Archivo. Establecer siempre que el comando **BACKUP** cambie y desactive el archivo. Valor: 0x20.  
  
 `_A_HIDDEN`  
 Archivo oculto. Generalmente no se ve con el comando DIR, a menos que use la opción **/AH** . Devuelve información acerca de los archivos normales y los que tienen este atributo. Valor: 0x02.  
  
 `_A_NORMAL`  
 Normal. El archivo no tiene otros atributos establecidos y puede leerse o escribirse sin restricciones. Valor: 0x00.  
  
 `_A_RDONLY`  
 Sólo lectura. No se puede abrir el archivo para escritura y no se puede crear un archivo con el mismo nombre. Valor: 0x01.  
  
 `_A_SUBDIR`  
 Subdirectorio. Valor: 0x10.  
  
 `_A_SYSTEM`  
 Archivo de sistema. Normalmente no se ven con el comando **DIR** , a menos que se use la opción **/A** o **/A:S** . Valor: 0x04.  
  
 `_findnext` busca el siguiente nombre, si procede, que coincida con el argumento `filespec` especificado en una llamada anterior a `_findfirst`. El argumento `fileinfo` debe apuntar a una estructura inicializada por la llamada anterior a `_findfirst`. Si se encuentra una coincidencia, el contenido de la estructura `fileinfo` se cambia como se describió anteriormente. En caso contrario, se deja sin modificar. `_findclose` cierra el identificador de búsqueda especificado y libera todos los recursos asociados para `_findfirst` y `_findnext`. El identificador devuelto por `_findfirst` o `_findnext` debe pasarse primero a `_findclose`, antes de realizar operaciones de modificación, como la eliminación, en los directorios que forman las rutas de acceso que se les pasan.  
  
 Puede anidar las funciones `_find` . Por ejemplo, si una llamada a `_findfirst` o `_findnext` descubre que el archivo es un subdirectorio, puede iniciarse una nueva búsqueda con otra llamada a `_findfirst` o `_findnext`.  
  
 `_wfindfirst` y `_wfindnext` son versiones con caracteres anchos de `_findfirst` y `_findnext`, respectivamente. El argumento de la estructura de las versiones de caracteres anchos tiene el tipo de datos `_wfinddata_t` , que se define en IO.h y en Wchar.h. Los campos de este tipo de datos son los mismos que los del tipo de datos `_finddata_t` , excepto que, en `_wfinddata_t` , el campo de nombre es de tipo `wchar_t` en lugar de ser de tipo `char`. De lo contrario, `_wfindfirst` y `_wfindnext` se comportan de forma idéntica a `_findfirst` y `_findnext`.  
  
 `_findfirst` y `_findnext` usan el tipo de tiempo de 64 bits. Si debe usar el tipo de tiempo de 32 bits anterior, puede definir `_USE_32BIT_TIME_T`. Las versiones de estas funciones que tienen el sufijo `32` en sus nombres usan el tipo de tiempo de 32 bits y aquellas con el sufijo `64` usan el tipo de tiempo de 64 bits.  
  
 Las funciones `_findfirst32i64`, `_findnext32i64`, `_wfindfirst32i64`y `_wfindnext32i64` también se comportan igual que las versiones de tipo de tiempo de 32 bits de estas funciones, excepto que usan y devuelven longitudes de archivos de 64 bits. Las funciones `_findfirst64i32`, `_findnext64i32`, `_wfindfirst64i32`y `_wfindnext64i32` usan el tipo de tiempo de 64 bits, pero usan longitudes de archivos de 32 bits. Estas funciones usan variaciones adecuadas del tipo `_finddata_t` en el que los campos tienen distintos tipos para el tamaño de archivo y la hora.  
  
 `_finddata_t` es realmente una macro que se evalúa en `_finddata64i32_t` (o `_finddata32_t` si `_USE_32BIT_TIME_T` está definido). En la siguiente tabla se resumen las versiones de `_finddata_t`:  
  
|Estructura|Tipo de tiempo|Tipo de tamaño de archivo|  
|---------------|---------------|--------------------|  
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|  
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|  
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|`__int64`|  
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|`__int64`|  
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|  
  
 `_fsize_t` es un `typedef` para `unsigned long` (32 bits).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_find.c  
// This program uses the 32-bit _find functions to print  
// a list of all files (and their attributes) with a .C extension  
// in the current directory.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <io.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _finddata_t c_file;  
   intptr_t hFile;  
  
   // Find first .c file in current directory   
   if( (hFile = _findfirst( "*.c", &c_file )) == -1L )  
      printf( "No *.c files in current directory!\n" );  
   else  
   {  
      printf( "Listing of .c files\n\n" );  
      printf( "RDO HID SYS ARC  FILE         DATE %25c SIZE\n", ' ' );  
      printf( "--- --- --- ---  ----         ---- %25c ----\n", ' ' );  
      do {  
         char buffer[30];  
         printf( ( c_file.attrib & _A_RDONLY ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_HIDDEN ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_SYSTEM ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_ARCH )   ? " Y  " : " N  " );  
         ctime_s( buffer, _countof(buffer), &c_file.time_write );  
         printf( " %-12s %.24s  %9ld\n",  
            c_file.name, buffer, c_file.size );  
      } while( _findnext( hFile, &c_file ) == 0 );  
      _findclose( hFile );  
   }  
}  
```  
  
```Output  
Listing of .c files  
  
RDO HID SYS ARC  FILE         DATE                           SIZE  
--- --- --- ---  ----         ----                           ----  
 N   N   N   Y   blah.c       Wed Feb 13 09:21:42 2002       1715  
 N   N   N   Y   test.c       Wed Feb 06 14:30:44 2002        312  
```  
  
## <a name="see-also"></a>Vea también  
 [Llamadas del sistema](../c-runtime-library/system-calls.md)