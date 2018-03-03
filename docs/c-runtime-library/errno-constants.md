---
title: errno (Constantes) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ENOEXEC
- ENOMEM
- E2BIG
- STRUNCATE
- ENOENT
- EMFILE
- EBADF
- EDEADLOCK
- EXDEV
- EILSEQ
- EINVAL
- EDOM
- EACCES
- ERANGE
- ENOSPC
- EAGAIN
- EEXIST
- ECHILD
dev_langs:
- C++
helpviewer_keywords:
- ENOEXEC constant
- EBADF constant
- EAGAIN constant
- EINVAL constant
- ENOENT constant
- errno constants
- E2BIG constant
- EMFILE constant
- EDEADLOCK constant
- ENOSPC constant
- EDOM constant
- ENOMEM constant
- EACCES constant
- EEXIST constant
- STRUNCATE constant
- ERANGE constant
- ECHILD constant
- EXDEV constant
- EILSEQ constant
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 98cc4c3afa245c55344454d4c96ea22d70905e0d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="errno-constants"></a>errno (Constantes)
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <errno.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 Los valores **errno** son constantes asignadas a [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) en caso de diversas condiciones de error.  
  
 ERRNO.H contiene las definiciones de los valores **errno**. Sin embargo, no todas las definiciones facilitadas en ERRNO.H se usan en sistemas operativos Windows de 32 bits. Algunos de los valores de ERRNO.H están presentes para mantener la compatibilidad con la familia UNIX de sistemas operativos.  
  
 Los valores **errno** en un sistema operativo Windows de 32 bits son un subconjunto de los valores de **errno** en sistemas XENIX. Por lo tanto, el valor **errno** no es necesariamente el mismo que el código de error real devuelto por una llamada del sistema de los sistemas operativos Windows. Para acceder al código de error real del sistema operativo, use la variable [_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), que contiene este valor.  
  
 Se admiten los siguientes valores **errno**:  
  
 **ECHILD**  
 No hay procesos de compilación.  
  
 **EAGAIN**  
 No hay más procesos. Error al intentar crear un proceso nuevo porque no hay más ranuras de proceso, o bien porque no hay suficiente memoria o porque se ha alcanzado el nivel máximo de anidamiento.  
  
 **E2BIG**  
 La lista de argumentos es demasiado larga.  
  
 **EACCES**  
 Permiso denegado. La configuración de permisos del archivo no permite el acceso especificado. Este error indica que se ha intentado acceder a un archivo, o, en algunos casos, a un directorio, de una manera que es incompatible con los atributos del archivo.  
  
 Por ejemplo, el error puede producirse cuando se realiza un intento de leer de un archivo que no está abierto, de abrir un archivo de solo lectura existente para escribir en él o de abrir un directorio en lugar de un archivo. En las versiones del sistema operativo MS-DOS 3.0 y posteriores, **EACCES** también puede indicar un bloqueo o infracción de uso compartido.  
  
 También puede producirse el error al intentar cambiar el nombre de un archivo o directorio o quitar un directorio existente.  
  
 **EBADF**  
 Número de archivo incorrecto. Hay dos causas posibles: 1) El descriptor de archivo especificado no es un valor válido o no hace referencia a un archivo abierto. 2) Se ha intentado escribir en un archivo o dispositivo abierto con acceso de solo lectura.  
  
 **EDEADLOCK**  
 Podría ocurrir un bloqueo irreversible del recurso. El argumento para una función matemática no está en el dominio de la función.  
  
 **EDOM**  
 Argumento matemático.  
  
 **EEXIST**  
 Existen archivos. Se intentó crear un archivo que ya existe. Por ejemplo, las marcas **_O_CREAT** y **_O_EXCL** se especifican en una llamada **_open**, pero el archivo especificado ya existe.  
  
 **EILSEQ**  
 Secuencia no válida de bytes (por ejemplo, en una cadena de MBCS).  
  
 **EINVAL**  
 Argumento no válido. Se asignó un valor no válido para uno de los argumentos a una función. Por ejemplo, el valor proporcionado para el origen al colocar un puntero de archivo (mediante una llamada a **fseek**) está antes del comienzo del archivo.  
  
 **EMFILE**  
 Demasiados archivos abiertos. No hay más descriptores de archivo disponibles, por lo que no se pueden abrir más archivos.  
  
 **ENOENT**  
 No existe ese archivo o directorio. El archivo o directorio especificado no existe o no se encuentra. Este mensaje puede aparecer cuando un archivo especificado no existe o un componente de una ruta de acceso no especifica un directorio existente.  
  
 **ENOEXEC**  
 Error de formato exec. Se intentó ejecutar un archivo que no es ejecutable o que tiene un formato de archivo ejecutable no válido.  
  
 **ENOMEM**  
 Memoria central insuficiente. No hay suficiente memoria disponible para el operador con el que se ha realizado el intento. Por ejemplo, este mensaje puede producirse cuando no hay suficiente memoria disponible para ejecutar un proceso secundario o cuando no se puede atender la solicitud de asignación de una llamada **_getcwd**.  
  
 **ENOSPC**  
 No queda espacio en el dispositivo. No hay más espacio disponible para escribir en el dispositivo (por ejemplo, cuando el disco está lleno).  
  
 **ERANGE**  
 El resultado es demasiado grande. Un argumento para una función matemática es demasiado grande, lo que causará una pérdida parcial o total de significación en el resultado. Este error puede producirse también en otras funciones cuando el argumento es mayor de lo esperado (por ejemplo, cuando el argumento *buffer* para **_getcwd** es más largo de lo esperado).  
  
 **EXDEV**  
 Vínculo de dispositivo cruzado. Se ha intentado mover un archivo a otro dispositivo (mediante la función **rename** ).  
  
 **STRUNCATE**  
 Una copia de la cadena o una concatenación generó una cadena truncada. Vea [_TRUNCATE](../c-runtime-library/truncate.md).  
  
 Se admiten los siguientes valores para la compatibilidad con Posix. Son los valores necesarios en los sistemas que no son Posix.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)