---
title: "_sopen_s, _wsopen_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_sopen_s"
  - "_wsopen_s"
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
  - "_sopen_s"
  - "wsopen_s"
  - "_wsopen_s"
  - "sopen_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_sopen_s (función)"
  - "_wsopen_s (función)"
  - "archivos [C++], abrir"
  - "archivos [C++], compartir"
  - "abrir archivos, para uso compartido"
  - "sopen_s (función)"
  - "wsopen_s (función)"
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# _sopen_s, _wsopen_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Abre un archivo para compartirlo.  Estas versiones de [\_sopen y \_wsopen](../../c-runtime-library/reference/sopen-wsopen.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _sopen_s(    int* pfh,    const char *filename,    int oflag,    int shflag,    int pmode ); errno_t _wsopen_s(    int* pfh,    const wchar_t *filename,    int oflag,    int shflag,    int pmode, );  
```  
  
#### Parámetros  
 \[out\] `pfh`  
 Identificador de archivo, o \-1 si se produce un error.  
  
 \[in\] `filename`  
 Nombre de archivo.  
  
 \[in\] `oflag`  
 Tipo de operaciones permitido.  
  
 \[in\] `shflag`  
 Tipo de uso compartido permitido.  
  
 \[in\] `pmode`  
 Configuración de permisos.  
  
## Valor devuelto  
 Un valor devuelto distinto de cero indica un error; en ese caso, `errno` se establece en uno de los siguientes valores.  
  
 `EACCES`  
 La ruta de acceso proporcionada es un directorio o el archivo es de solo lectura, pero se intentó realizar una operación de abrir para escribir.  
  
 `EEXIST`  
 Las marcas `_O_CREAT` y `_O_EXCL` se han especificado, pero `filename` ya existe.  
  
 `EINVAL`  
 Argumento `oflag`, `shflag` o `pmode` no válido, o bien `pfh` o `filename` era un puntero nulo.  
  
 `EMFILE`  
 No hay más descriptores de archivo disponibles.  
  
 `ENOENT`  
 No se encuentra el archivo o la ruta de acceso.  
  
 Si se pasa un argumento no válido a la función, se invocará al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y se devuelve `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 En caso de error, se devuelve \-1 a través de `pfh` \(a menos que `pfh` sea un puntero nulo\).  
  
## Comentarios  
 La función `_sopen_s` abre el archivo especificado por `filename` y lo prepara para una lectura o escritura compartida, como establecen las marcas `oflag` y `shflag`.  `_wsopen_s` es una versión con caracteres anchos de `_sopen_s`; el argumento `filename` para `_wsopen_s` es una cadena de caracteres anchos.  Por lo demás, `_wsopen_s` y `_sopen_s` se comportan de forma idéntica.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tsopen_s`|`_sopen_s`|`_sopen_s`|`_wsopen_s`|  
  
 La expresión de entero `oflag` se forma combinando una o más constantes de manifiesto, que están definidas en \<fcntl.h\>.  Cuando dos o más constantes forman el argumento `oflag`, se combinan con el operador bit a bit OR \(`|`\).  
  
 `_O_APPEND`  
 Recoloca un puntero de archivo al final del archivo antes de cada operación de escritura.  
  
 `_O_BINARY`  
 Abre un archivo en modo binario \(sin traducir\).  \(Vea [fopen](../../c-runtime-library/reference/fopen-wfopen.md) para ver una descripción del modo binario\).  
  
 `_O_CREAT`  
 Crea un archivo y lo abre para escribir en él.  No tiene ningún efecto si el archivo especificado por `filename` existe.  
  
 `_O_CREAT | _O_SHORT_LIVED`  
 Crea un archivo temporal y, si es posible, no se vuelca en el disco.  
  
 `_O_CREAT | _O_TEMPORARY`  
 Crea un archivo temporal. El archivo se elimina cuando se cierra el último descriptor de archivo.  
  
 `_O_CREAT | _O_EXCL`  
 Devuelve un valor de error si el archivo especificado por `filename` existe.  Válido únicamente cuando se usa con `_O_CREAT`.  
  
 `_O_NOINHERIT`  
 Impide que se cree un descriptor de archivo compartido.  
  
 `_O_RANDOM`  
 Especifica un acceso principalmente aleatorio desde el disco.  
  
 `_O_RDONLY`  
 Abre un archivo únicamente para leerlo.  No se puede especificar con `_O_RDWR` o `_O_WRONLY`.  
  
 `_O_RDWR`  
 Abre un archivo tanto para lectura como para escritura.  No se puede especificar con `_O_RDONLY` o `_O_WRONLY`.  
  
 `_O_SEQUENTIAL`  
 Especifica un acceso principalmente secuencial desde el disco.  
  
 `_O_TEXT`  
 Abre un archivo en modo de texto \(traducido\).  Para más información, vea los temas sobre [E\/S de archivo en modo binario y de texto](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [fopen](../../c-runtime-library/reference/fopen-wfopen.md)\).  
  
 `_O_TRUNC`  
 Abre un archivo y lo trunca a longitud cero. El archivo debe tener permiso de escritura.  No se puede especificar con `_O_RDONLY`.  Cuando `_O_TRUNC` se usa con `_O_CREAT`, se abre un archivo existente o se crea uno.  
  
> [!NOTE]
>  La marca `_O_TRUNC` destruye el contenido del archivo especificado.  
  
 `_O_WRONLY`  
 Abre un archivo únicamente para escribir en él.  No se puede especificar con `_O_RDONLY` o `_O_RDWR`.  
  
 `_O_U16TEXT`  
 Abre un archivo en modo Unicode UTF\-16.  
  
 `_O_U8TEXT`  
 Abre un archivo en modo Unicode UTF\-8.  
  
 `_O_WTEXT`  
 Abre un archivo en modo Unicode.  
  
 Para especificar el modo de acceso a archivos, se debe especificar `_O_RDONLY`, `_O_RDWR` o `_O_WRONLY`.  No existe un valor predeterminado para el modo de acceso.  
  
 Cuando un archivo se abre en modo Unicode con `_O_WTEXT`, `_O_U8TEXT` o `_O_U16TEXT`, las funciones de entrada traducen los datos leídos de dicho archivo a datos UTF\-16 almacenados como de tipo `wchar_t`.  Las funciones que escriben en un archivo abierto en modo Unicode esperan que haya búferes que contengan datos UTF\-16 almacenados como de tipo `wchar_t`.  Si el archivo está codificado como UTF\-8, los datos UTF\-16 se traducen a UTF\-8 cuando se escriben, y el contenido codificado en UTF\-8 del archivo se traduce a UTF\-16 cuando se lee.  Si se intenta leer o escribir un número impar de bytes en el modo Unicode, se producirá un error de validación de parámetros.  Para leer o escribir datos almacenados en el programa como UTF\-8, use un modo de archivo binario o de texto en lugar de un modo Unicode.  Cualquier traducción de codificación que sea necesaria es su responsabilidad.  
  
 Si se llama a `_sopen_s` con `_O_WRONLY | _O_APPEND` \(modo Anexar\) y `_O_WTEXT`, `_O_U16TEXT` o `_O_U8TEXT`, primero se intentará abrir el archivo para lectura y escritura, leer la BOM y, luego, volver a abrirlo únicamente para escritura.  Si no se puede abrir el archivo para lectura y escritura, abre el archivo solamente para escritura y usa el valor predeterminado como opción del modo Unicode.  
  
 El argumento `shflag` es una expresión constante compuesta por una de las constantes de manifiesto siguientes, que se definen \<share.h\>.  
  
 `_SH_DENYRW`  
 Deniega el acceso de lectura y escritura a un archivo.  
  
 `_SH_DENYWR`  
 Deniega el acceso de escritura a un archivo.  
  
 `_SH_DENYRD`  
 Deniega el acceso de lectura a un archivo.  
  
 `_SH_DENYNO`  
 Permite el acceso de lectura y escritura.  
  
 El argumento `pmode` siempre es necesario, cosa que no sucede con `_sopen`.  Cuando `_O_CREAT` se especifica, si el archivo no existe, `pmode` especifica la configuración de permisos del archivo, que se establece cuando el nuevo archivo se cierra por primera vez.  De lo contrario, `pmode` se omite.  `pmode` es una expresión de entero que contiene una o ambas constantes del manifiesto \(`_S_IWRITE` y `_S_IREAD`\), definidas en \<sys\\stat.h\>.  Cuando ambas constantes se proporcionan, se combinan con el operador bit a bit OR.  El significado de `pmode` es el que se indica a continuación.  
  
 `_S_IWRITE`  
 Escritura permitida.  
  
 `_S_IREAD`  
 Lectura permitida.  
  
 `_S_IREAD | _S_IWRITE`  
 Lectura y escritura permitidas.  
  
 Si no se ha concedido el permiso de escritura, el archivo será de solo lectura.  En el sistema operativo Windows, todos los archivos se pueden leer; es decir, no se puede conceder permisos únicamente de escritura.  En consecuencia, los modos `_S_IWRITE` y `_S_IREAD | _S_IWRITE` son equivalentes.  
  
 `_sopen_s` aplica la máscara de permisos de archivo actual a `pmode` antes de que los permisos se hayan definido.  \(Vea [\_umask](../../c-runtime-library/reference/umask.md)\).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_sopen_s`|\<io.h\>|\<fcntl.h\>, \<sys\\types.h\>, \<sys\\stat.h\>, \<share.h\>|  
|`_wsopen_s`|\<io.h\> o \<wchar.h\>|\<fcntl.h\>, \<sys\/types.h\>, \<sys\/stat.h\>, \<share.h\>|  
  
 `_sopen_s` y `_wsopen_s` son extensiones de Microsoft.  Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [\_locking](../../c-runtime-library/reference/locking.md).  
  
## Vea también  
 [E\/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_fsopen, \_wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)