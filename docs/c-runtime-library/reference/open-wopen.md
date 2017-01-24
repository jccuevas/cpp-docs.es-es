---
title: "_open, _wopen | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_open"
  - "_wopen"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wopen"
  - "_topen"
  - "_open"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_open (función)"
  - "_topen (función)"
  - "_wopen (función)"
  - "archivos [C++], abrir"
  - "open (función)"
  - "abrir archivos, para E/S de archivo"
  - "topen (función)"
  - "wopen (función)"
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _open, _wopen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Abre un archivo.  Estas funciones están desusadas porque existen versiones más seguras; vea [\_sopen\_s, \_wsopen\_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md).  
  
## Sintaxis  
  
```  
int _open(  
   const char *filename,  
   int oflag [,  
   int pmode]   
);  
int _wopen(  
   const wchar_t *filename,  
   int oflag [,  
   int pmode]   
);  
```  
  
#### Parámetros  
 `filename`  
 Nombre de archivo.  
  
 `oflag`  
 Tipo de operaciones permitido.  
  
 `pmode`  
 Modo de permiso.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un descriptor de archivo correspondiente al archivo abierto.  Un valor devuelto de \-1 indica un error; en ese caso, `errno` se establece en uno de los siguientes valores.  
  
 `EACCES`  
 Se intentó abrir un archivo de solo lectura para escribir en él, el modo de uso compartido del archivo no permite las operaciones especificadas o la ruta de acceso indicada es un directorio.  
  
 `EEXIST`  
 Las marcas `_O_CREAT` y `_O_EXCL` se han especificado, pero `filename` ya existe.  
  
 `EINVAL`  
 Argumentos `oflag` o `pmode` no válidos.  
  
 `EMFILE`  
 No hay más descriptores de archivo disponibles \(hay demasiados archivos abiertos\).  
  
 `ENOENT`  
 No se encuentra el archivo o la ruta de acceso.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `_open` abre el archivo especificado por `filename` y lo prepara para su lectura o escritura, tal y como establece la marca `oflag`.  `_wopen` es una versión con caracteres anchos de `_open`; el argumento `filename` para `_wopen` es una cadena de caracteres anchos.  Por lo demás, `_wopen` y `_open` se comportan de forma idéntica.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_topen`|`_open`|`_open`|`_wopen`|  
  
 `oflag` es una expresión de entero formada por una o varias de las siguientes constantes del manifiesto o combinaciones de constantes, definidas en \<fcntl.h\>.  
  
 `_O_APPEND`  
 Mueve un puntero de archivo al final del archivo antes de cada operación de escritura.  
  
 `_O_BINARY`  
 Abre el archivo en modo binario \(sin traducir\).  \(Vea [fopen](../../c-runtime-library/reference/fopen-wfopen.md) para ver una descripción del modo binario\).  
  
 `_O_CREAT`  
 Crea un archivo y lo abre para escribir en él.  No tiene ningún efecto si el archivo especificado por `filename` existe.  El argumento `pmode` es necesario cuando `_O_CREAT` se especifica.  
  
 `_O_CREAT` &#124; `_O_SHORT_LIVED`  
 Crea un archivo temporal y, si es posible, no se vuelca en el disco.  El argumento `pmode` es necesario cuando `_O_CREAT` se especifica.  
  
 `_O_CREAT` &#124; `_O_TEMPORARY`  
 Crea un archivo temporal. El archivo se elimina cuando se cierra el último descriptor de archivo.  El argumento `pmode` es necesario cuando `_O_CREAT` se especifica.  
  
 `_O_CREAT` &#124; `_O_EXCL`  
 Devuelve un valor de error si el archivo especificado por `filename` existe.  Válido únicamente cuando se usa con `_O_CREAT`.  
  
 `_O_NOINHERIT`  
 Impide que se cree un descriptor de archivo compartido.  
  
 `_O_RANDOM`  
 Especifica que el almacenamiento en caché está optimizado para el acceso aleatorio \(pero no restringido a este\) desde el disco.  
  
 `_O_RDONLY`  
 Abre un archivo únicamente para leerlo.  No se puede especificar con `_O_RDWR` o `_O_WRONLY`.  
  
 `_O_RDWR`  
 Abre el archivo para lectura y escritura.  No se puede especificar con `_O_RDONLY` o `_O_WRONLY`.  
  
 `_O_SEQUENTIAL`  
 Especifica que el almacenamiento en caché está optimizado para el acceso secuencial \(pero no restringido a este\) desde el disco.  
  
 `_O_TEXT`  
 Abre un archivo en modo de texto \(traducido\).  Para más información, vea los temas sobre [E\/S de archivo en modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [fopen](../../c-runtime-library/reference/fopen-wfopen.md)\).  
  
 `_O_TRUNC`  
 Abre un archivo y lo trunca a longitud cero. El archivo debe tener permiso de escritura.  No se puede especificar con `_O_RDONLY`.  Cuando `_O_TRUNC` se usa con `_O_CREAT`, se abre un archivo existente o se crea uno.  
  
> [!NOTE]
>  La marca `_O_TRUNC` destruye el contenido del archivo especificado.  
  
 `_O_WRONLY`  
 Abre el archivo únicamente para escribir en él.  No se puede especificar con `_O_RDONLY` o `_O_RDWR`.  
  
 `_O_U16TEXT`  
 Abre el archivo en modo Unicode UTF\-16.  
  
 `_O_U8TEXT`  
 Abre el archivo en modo Unicode UTF\-8.  
  
 `_O_WTEXT`  
 Abre el archivo en modo Unicode.  
  
 Para especificar el modo de acceso a archivos, se debe especificar `_O_RDONLY`, `_O_RDWR` o `_O_WRONLY`.  No existe un valor predeterminado para el modo de acceso.  
  
 Si se usa `_O_WTEXT` para abrir un archivo para leerlo, `_open` lee el principio del archivo y busca una marca BOM.  Si hay una BOM, el archivo se considera como UTF\-8 o UTF\-16LE \(esto depende de la BOM\).  Si no hay BOM, el archivo se considera ANSI.  Cuando se usa `_O_WTEXT` para abrir un archivo para su escritura, se usa UTF\-16.  Independientemente de la marca BOM o configuración que existiera anteriormente, si se usa `_O_U8TEXT`, el archivo siempre se abrirá como UTF\-8; por su parte, si se usa `_O_U16TEXT`, el archivo siempre se abrirá como UTF\-16.  
  
 Cuando un archivo se abre en modo Unicode con `_O_WTEXT`, `_O_U8TEXT` o `_O_U16TEXT`, las funciones de entrada traducen los datos leídos de dicho archivo a datos UTF\-16 almacenados como de tipo `wchar_t`.  Las funciones que escriben en un archivo abierto en modo Unicode esperan que haya búferes que contengan datos UTF\-16 almacenados como de tipo `wchar_t`.  Si el archivo está codificado como UTF\-8, los datos UTF\-16 se traducen a UTF\-8 cuando se escriben, y el contenido codificado en UTF\-8 del archivo se traduce a UTF\-16 cuando se lee.  Si se intenta leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de validación de parámetros.  Para leer o escribir datos almacenados en el programa como UTF\-8, use un modo de archivo binario o de texto en lugar de un modo Unicode.  Cualquier traducción de codificación que sea necesaria es su responsabilidad.  
  
 Si se llama a `_open` con `_O_WRONLY|_O_APPEND` \(modo Anexar\) y `_O_WTEXT`, `_O_U16TEXT` o `_O_U8TEXT`, primero se intentará abrir el archivo para lectura y escritura, leer la BOM y, luego, volver a abrirlo únicamente para escritura.  Si no se puede abrir el archivo para lectura y escritura, abre el archivo solamente para escritura y usa el valor predeterminado como opción del modo Unicode.  
  
 Cuando se usan dos o más constantes del manifiesto para formar el argumento `oflag`, estas constantes se combinan con el operador bit a bit OR \(                       `|` \).  Para más información sobre los modos de texto y binario, vea [E\/S de archivo de modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
 El argumento `pmode` es necesario únicamente cuando `_O_CREAT` se especifica.  Si el archivo ya existe, `pmode` se omite.  De lo contrario, `pmode` especifica la configuración de permisos del archivo, que se establece cuando el nuevo archivo se cierra por primera vez.  `_open` aplica la máscara de permisos de archivo actual a `pmode` antes de que los permisos se hayan definido.  \(Para más información, vea [\_umask](../../c-runtime-library/reference/umask.md)\). `pmode` es una expresión de entero que contiene una o las dos constantes del manifiesto siguientes, definidas en \<sys\\stat.h\>.  
  
 `_S_IREAD`  
 Solo se permite la lectura.  
  
 `_S_IWRITE`  
 Escritura permitida.  \(De hecho, se permiten la lectura y escritura\).  
  
 `_S_IREAD`  `|`  `_S_IWRITE`  
 Lectura y escritura permitidas.  
  
 Cuando ambas constantes se proporcionan, se unen al operador bit a bit OR \(                       `|` \).  En Windows, todos los archivos se pueden leer; es decir, el permiso de solo escritura no está disponible.  En consecuencia, los modos `_S_IWRITE` y `_S_IREAD` `|` `_S_IWRITE` son equivalentes.  
  
 Tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md), la función genera una aserción en modo de depuración e invoca a un controlador de parámetros incorrecto si se especifica un valor distinto de cualquier combinación de `_S_IREAD` y `_S_IWRITE` para `pmode` \(aun cuando se especifique un `pmode` válido en otro sistema operativo\), o si se especifica un valor distinto a los valores de `oflag` permitidos.  Si la ejecución puede continuar, la función devuelve \-1 y establece `errno` en `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_open`|\<io.h\>|\<fcntl.h\>, \<sys\\types.h\>, \<sys\\stat.h\>|  
|`_wopen`|\<io.h\> o \<wchar.h\>|\<fcntl.h\>, \<sys\\types.h\>, \<sys\\stat.h\>|  
  
 `_open` y `_wopen` son extensiones de Microsoft.  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_open.c  
// compile with: /W3  
/* This program uses _open to open a file  
 * named CRT_OPEN.C for input and a file named CRT_OPEN.OUT  
 * for output. The files are then closed.  
 */  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int fh1, fh2;  
  
   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996  
   // Note: _open is deprecated; consider using _sopen_s instead  
   if( fh1 == -1 )  
      perror( "Open failed on input file" );  
   else  
   {  
      printf( "Open succeeded on input file\n" );  
      _close( fh1 );  
   }  
  
   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |   
                            _S_IWRITE ); // C4996  
   if( fh2 == -1 )  
      perror( "Open failed on output file" );  
   else  
   {  
      printf( "Open succeeded on output file\n" );  
      _close( fh2 );  
   }  
}  
```  
  
## Salida  
  
```  
Open succeeded on input file  
Open succeeded on output file  
```  
  
## Equivalente en .NET Framework  
  
-   [System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)  
  
-   <xref:System.IO.FileStream.%23ctor%2A>  
  
## Vea también  
 [E\/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [\_chmod, \_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_dup, \_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_sopen, \_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)