---
title: errno, _doserrno, _sys_errlist y _sys_nerr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _errno
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _sys_errlist
- errno
- _sys_nerr
- _doserrno
dev_langs:
- C++
helpviewer_keywords:
- error codes, printing
- sys_errlist global variable
- doserrno global variable
- errno global variable
- _doserrno global variable
- _sys_errlist global variable
- _sys_nerr global variable
- sys_nerr global variable
ms.assetid: adbec641-6d91-4e19-8398-9a34046bd369
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b17abb975ea9f3212d4bd6171bcd2bffb78e483c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392424"
---
# <a name="errno-doserrno-syserrlist-and-sysnerr"></a>errno, _doserrno, _sys_errlist y _sys_nerr
Macros globales que contienen códigos de error que se establecen durante la ejecución del programa, así como los equivalentes de cadena de esos códigos para mostrarlos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#define errno   (*_errno())  
#define _doserrno   (*__doserrno())  
#define _sys_errlist (__sys_errlist())  
#define _sys_nerr (*__sys_nerr())  
```  
  
## <a name="remarks"></a>Comentarios  
 El runtime establece en 0 `errno` y `_doserrno` durante el inicio del programa. `errno` se establece en un error en una llamada de nivel del sistema. Puesto que `errno` contiene el valor de la última llamada que la estableció, las llamadas posteriores pueden cambiar este valor. Llamadas de la biblioteca en tiempo de ejecución que establecen `errno` en un error no borran `errno` si la operación se realiza correctamente. Borre siempre `errno` llamando a `_set_errno(0)` inmediatamente antes de que una llamada pueda establecerlo, y compruébelo inmediatamente después de la llamada.  
  
 Si se produce un error, `errno` no se establece necesariamente en el mismo valor que el código de error devuelto por una llamada del sistema. En operaciones de E/S, `_doserrno` almacena los equivalentes de código de error del sistema operativo de los códigos de `errno`. En la mayoría de las operaciones que no son de E/S, el valor de `_doserrno` no se establece.  
  
 Cada valor de `errno` se asocia a un mensaje de error en `_sys_errlist` que se puede imprimir mediante una de las funciones [perror](../c-runtime-library/reference/perror-wperror.md) o almacenar en una cadena mediante las funciones [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) o [strerror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md). Las funciones `perror` y `strerror` usan la matriz `_sys_errlist` y `_sys_nerr` (número de elementos en `_sys_errlist`) para procesar la información del error. El acceso directo a `_sys_errlist` y `_sys_nerr` está en desuso por motivos de seguridad de código. Se recomienda usar las versiones funcionales y más seguras en lugar de emplear macros globales, como se muestra aquí:  
  
|Macro global|Equivalentes funcionales|  
|------------------|----------------------------|  
|`_doserrno`|[_get_doserrno](../c-runtime-library/reference/get-doserrno.md), [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)|  
|`errno`|[_get_errno](../c-runtime-library/reference/get-errno.md), [_set_errno](../c-runtime-library/reference/set-errno.md)|  
|`_sys_errlist`, `_sys_nerr`|[strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|  
  
 Las rutinas matemáticas de la biblioteca establecen `errno` llamando a [_matherr](../c-runtime-library/reference/matherr.md). Para controlar los errores matemáticos de otra manera, escriba su propia rutina de acuerdo con la descripción de referencia de `_matherr` y asígnele el nombre `_matherr`.  
  
 Todos los valores de `errno` de la siguiente tabla son constantes predefinidas en \<errno.h>> y son compatibles con UNIX. Solo `ERANGE`, `EILSEQ` y `EDOM` se especifican en el estándar ISO C99.  
  
|Constante|Mensaje de error del sistema|Valor|  
|--------------|--------------------------|-----------|  
|`EPERM`|Operación no permitida|1|  
|`ENOENT`|No existe ese archivo o directorio|2|  
|`ESRCH`|No existe tal proceso|3|  
|`EINTR`|Función interrumpida|4|  
|`EIO`|Error de E/S|5|  
|`ENXIO`|No existe tal dispositivo o dirección|6|  
|`E2BIG`|Lista de argumentos demasiado larga|7|  
|`ENOEXEC`|Error de formato exec|8|  
|`EBADF`|Número de archivo incorrecto|9|  
|`ECHILD`|No hay procesos de compilación|10|  
|`EAGAIN`|No hay más procesos, memoria insuficiente o se alcanzó el nivel de anidamiento máximo|11|  
|`ENOMEM`|Memoria insuficiente|12|  
|`EACCES`|Permiso denegado|13|  
|`EFAULT`|Dirección incorrecta|14|  
|`EBUSY`|Dispositivo o recurso no disponible|16|  
|`EEXIST`|El archivo existe|17|  
|`EXDEV`|Vínculo de dispositivo cruzado|18|  
|`ENODEV`|No existe tal dispositivo|19|  
|`ENOTDIR`|No es un directorio|20|  
|`EISDIR`|Es un directorio|21|  
|`EINVAL`|Argumento no válido|22|  
|`ENFILE`|Demasiados archivos abiertos en el sistema|23|  
|`EMFILE`|Demasiados archivos abiertos|24|  
|`ENOTTY`|Operación de control de E/S incorrecta|25|  
|`EFBIG`|Archivo demasiado grande|27|  
|`ENOSPC`|No queda espacio en el dispositivo|28|  
|`ESPIPE`|Búsqueda no válida|29|  
|`EROFS`|Sistema de archivos de solo lectura|30|  
|`EMLINK`|Hay demasiados vínculos|31|  
|`EPIPE`|Canalización rota|32|  
|`EDOM`|Argumento matemático|33|  
|`ERANGE`|El resultado es demasiado grande|34|  
|`EDEADLK`|Podría ocurrir un bloqueo irreversible del recurso|36|  
|`EDEADLOCK`|Igual que EDEADLK por compatibilidad con versiones anteriores de Microsoft C|36|  
|`ENAMETOOLONG`|El nombre de archivo es demasiado largo|38|  
|`ENOLCK`|No hay bloqueos disponibles|39|  
|`ENOSYS`|Función no admitida|40|  
|`ENOTEMPTY`|El directorio no está vacío|41|  
|`EILSEQ`|Secuencia de bytes no válida|42|  
|`STRUNCATE`|Se truncó la cadena|80|  
  
## <a name="requirements"></a>Requisitos  
  
|Macro global|Encabezado necesario|Encabezado opcional|  
|------------------|---------------------|---------------------|  
|`errno`|\<errno.h> o \<stdlib.h>, \<cerrno> o \<cstdlib> (C++)||  
|`_doserrno`, `_sys_errlist`, `_sys_nerr`|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|  
  
 Las macros `_doserrno`, `_sys_errlist` y `_sys_nerr` son extensiones de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Variables globales](../c-runtime-library/global-variables.md)   
 [errno (constantes)](../c-runtime-library/errno-constants.md)   
 [perror, _wperror](../c-runtime-library/reference/perror-wperror.md)   
 [strerror, _strerror, _wcserror, \__wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)   
 [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)   
 [_get_doserrno](../c-runtime-library/reference/get-doserrno.md)   
 [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)   
 [_get_errno](../c-runtime-library/reference/get-errno.md)   
 [_set_errno](../c-runtime-library/reference/set-errno.md)