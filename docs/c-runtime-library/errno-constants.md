---
title: "errno (Constantes) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENOEXEC"
  - "ENOMEM"
  - "E2BIG"
  - "STRUNCATE"
  - "ENOENT"
  - "EMFILE"
  - "EBADF"
  - "EDEADLOCK"
  - "EXDEV"
  - "EILSEQ"
  - "EINVAL"
  - "EDOM"
  - "EACCES"
  - "ERANGE"
  - "ENOSPC"
  - "EAGAIN"
  - "EEXIST"
  - "ECHILD"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "E2BIG (constante)"
  - "EACCES (constante)"
  - "EAGAIN (constante)"
  - "EBADF (constante)"
  - "ECHILD (constante)"
  - "EDEADLOCK (constante)"
  - "EDOM (constante)"
  - "EEXIST (constante)"
  - "EILSEQ (constante)"
  - "EINVAL (constante)"
  - "EMFILE (constante)"
  - "ENOENT (constante)"
  - "ENOEXEC (constante)"
  - "ENOMEM (constante)"
  - "ENOSPC (constante)"
  - "ERANGE (constante)"
  - "errno (constantes)"
  - "EXDEV (constante)"
  - "STRUNCATE (constante)"
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# errno (Constantes)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <errno.h>  
```  
  
## Comentarios  
 Los valores de **errno** son constantes asignadas a [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) en caso de varias condiciones de error.  
  
 ERRNO.H contiene las definiciones de los valores de **errno** .  Sin embargo, no todas las definiciones incluidas en ERRNO.H se utilizan en sistemas operativos Windows de 32 bits.  Algunos de los valores de ERRNO.H están presentes mantener la compatibilidad con la familia de UNIX de sistemas operativos.  
  
 Los valores de **errno** en un sistema operativo Windows de 32 bits son un subconjunto de valores para **errno** en sistemas de XENIX.  Así, el valor de **errno** no es necesariamente el mismo que el código de error real devuelto por una llamada al sistema de los sistemas operativos Windows.  Para tener acceso al código de error real del sistema operativo, utilice la variable de [\_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , que contiene este valor.  
  
 Se admiten los siguientes valores de **errno** :  
  
 **ECHILD**  
 Los procesos de generación.  
  
 **EAGAIN**  
 No varios procesos.  Un intento de crear un nuevo proceso produjo un error porque no hay ranuras de proceso, o no hay suficiente memoria, o se ha alcanzado el nivel de anidamiento máximo.  
  
 **E2BIG**  
 Lista de argumentos es demasiado largo.  
  
 **EACCES**  
 Permiso denegado.  La configuración de permisos del archivo no permite el acceso especificado.  Este error significa que se realizó un intento de obtener acceso a un archivo \(o, en algunos casos, un directorio\) de forma no compatible con los atributos de archivo.  
  
 Por ejemplo, el error puede producirse cuando se realiza un intento de leer de un archivo que no está abierto, para abrir un archivo de sólo lectura existente para escribir, o abrir un directorio en lugar de un archivo.  En las versiones 3.0 del sistema operativo MS\-DOS y después, **EACCES** también puede indicar un bloqueo o una infracción de uso compartido.  
  
 El error puede aparecer también en un intento de cambiar el nombre de un archivo o directorio o quitar un directorio existente.  
  
 **EBADF**  
 Número de archivo incorrecto.  Hay dos causas posibles: 1\) El archivo especificado descriptor de no es un valor válido ni hace referencia a un archivo abierto. 2\) Se intentó para escribir en un archivo o el dispositivo abierto para acceso de sólo lectura.  
  
 **EDEADLOCK**  
 El interbloqueo de recursos aparecería.  El argumento de una función matemática no está en el dominio de la función.  
  
 **EDOM**  
 Argumento de matemáticas.  
  
 **EEXIST**  
 Los archivos existen.  Se ha creado un intento de crear un archivo que ya existe.  Por ejemplo, **\_O\_CREAT** e indicadores de **\_O\_EXCL** se especifican en una llamada de **\_open** , pero el archivo con nombre ya existe.  
  
 **EILSEQ**  
 Secuencia de bytes no válida \(por ejemplo, en una cadena de MBCS\).  
  
 **EINVAL**  
 Argumento no válido.  Un valor no válido se especificado para uno de los argumentos de una función.  Por ejemplo, el valor especificado para el origen cuando la posición de un puntero de archivo \(mediante una llamada a **fseek**\) es anterior al principio del archivo.  
  
 **EMFILE**  
 Demasiados archivos abiertos.  No más de descriptores de archivo están disponibles, por lo que no más de archivos pueden abrir.  
  
 **ENOENT**  
 Dicho archivo o directorio.  El archivo o el directorio especificado no existe o no se encuentra.  Este mensaje puede producirse cuando no existe un archivo especificado o un componente de un trazado no especifica un directorio existente.  
  
 **ENOEXEC**  
 Error de formato exec.  Se realizó un intento de ejecutar un archivo que no es ejecutable o que tiene un formato de archivo ejecutable no válido.  
  
 **ENOMEM**  
 No hay base.  Memoria insuficiente está disponible para el operador frustrado.  Por ejemplo, este mensaje puede aparecer cuando la memoria insuficiente está disponible ejecutar un proceso secundario, o cuando la solicitud de asignación en una llamada de **\_getcwd** no puede satisfacer.  
  
 **ENOSPC**  
 Ningún espacio está en el dispositivo.  No más de espacio para escribir está disponible en el dispositivo \(por ejemplo, cuando el disco está lleno\).  
  
 **ERANGE**  
 Resultado demasiado grande.  Un argumento de una función matemática es demasiado grande, lo que da como resultado la pérdida de significado parcial o total en el resultado.  Este error también puede producirse en otras funciones cuando un argumento es mayor que esperado \(por ejemplo, cuando el argumento *del búfer* a **\_getcwd** es más tiempo de lo esperado\).  
  
 **EXDEV**  
 Enlace a otro dispositivo.  Se intentó de mover un archivo a otro dispositivo \(mediante la función de **rename** \).  
  
 **STRUNCATE**  
 Una copia o una concatenación de cadenas daba lugar a una cadena truncada.  Vea [\_TRUNCATE](../c-runtime-library/truncate.md).  
  
 Los valores siguientes se admiten por compatibilidad con POSIX.  Son valores necesarios en los sistemas de no POSIX.  
  
```  
#define E2BIG [argument list too long]  
#define EACCES [permission denied]  
#define EADDRINUSE [address in use]  
#define EADDRNOTAVAIL [address not available]  
#define EAFNOSUPPORT [address family not supported]  
#define EAGAIN [resource unavailable try again]  
#define EALREADY [connection already in progress]  
#define EBADF [bad file descriptor]  
#define EBADMSG [bad message]  
#define EBUSY [device or resource busy]  
#define ECANCELED [operation canceled]  
#define ECHILD [no child process]  
#define ECONNABORTED [connection aborted]  
#define ECONNREFUSED [connection refused]  
#define ECONNRESET [connection reset]  
#define EDEADLK [resource deadlock would occur]  
#define EDESTADDRREQ [destination address required]  
#define EDOM [argument out of domain]  
#define EEXIST [file exists]  
#define EFAULT [bad address]  
#define EFBIG [file too large]  
#define EHOSTUNREACH [host unreachable]  
#define EIDRM [identifier removed]  
#define EILSEQ [illegal byte sequence]  
#define EINPROGRESS [operation in progress]  
#define EINTR [interrupted]  
#define EINVAL [invalid argument]  
#define EIO [io error]  
#define EISCONN [already connected]  
#define EISDIR [is a directory]  
#define ELOOP [too many synbolic link levels]  
#define EMFILE [too many files open]  
#define EMLINK [too many links]  
#define EMSGSIZE [message size]  
#define ENAMETOOLONG [filename too long]  
#define ENETDOWN [network down]  
#define ENETRESET [network reset]  
#define ENETUNREACH [network unreachable]  
#define ENFILE [too many files open in system]  
#define ENOBUFS [no buffer space]  
#define ENODATA [no message available]  
#define ENODEV [no such device]  
#define ENOENT [no such file or directory]  
#define ENOEXEC [executable format error]  
#define ENOLCK [no lock available]  
#define ENOLINK [no link]  
#define ENOMEM [not enough memory]  
#define ENOMSG [no message]  
#define ENOPROTOOPT [no protocol option]  
#define ENOSPC [no space on device]  
#define ENOSR [no stream resources]  
#define ENOSTR [not a stream]  
#define ENOSYS [function not supported]  
#define ENOTCONN [not connected]  
#define ENOTDIR [not a directory]  
#define ENOTEMPTY [directory not empty]  
#define ENOTRECOVERABLE [state not recoverable]  
#define ENOTSOCK [not a socket]  
#define ENOTSUP [not supported]  
#define ENOTTY [inappropriate io control operation]  
#define ENXIO [no such device or address]  
#define EOPNOTSUPP [operation not supported]  
#define EOTHER [other]  
#define EOVERFLOW [value too large]  
#define EOWNERDEAD [owner dead]  
#define EPERM [operation not permitted]  
#define EPIPE [broken pipe]  
#define EPROTO [protocol error]  
#define EPROTONOSUPPORT [protocol not supported]  
#define EPROTOTYPE [wrong protocol type]  
#define ERANGE [result out of range]  
#define EROFS [read only file system]  
#define ESPIPE [invalid seek]  
#define ESRCH [no such process]  
#define ETIME [stream timeout]  
#define ETIMEDOUT [timed out]  
#define ETXTBSY [text file busy]  
#define EWOULDBLOCK [operation would block]  
#define EXDEV [cross device link]  
```  
  
## Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)