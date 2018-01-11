---
title: _dupenv_s, _wdupenv_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
dev_langs: C++
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e17ff0c468f3b99a1c97114c93ea64ecfa9499e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s, _wdupenv_s
Obtiene un valor del entorno actual.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _dupenv_s(  
   char **buffer,  
   size_t *numberOfElements,  
   const char *varname  
);  
errno_t _wdupenv_s(  
   wchar_t **buffer,  
   size_t *numberOfElements,  
   const wchar_t *varname  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `buffer`  
 Búfer en el que se va a almacenar el valor de la variable.  
  
 `numberOfElements`  
 Tamaño de `buffer`.  
  
 `varname`  
 Nombre de la variable de entorno.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
 Estas funciones validan sus parámetros; si `buffer` o `varname` es `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
 Si estas funciones no pueden asignar suficiente memoria, establecen `buffer` en `NULL` y `numberOfElements` en 0, y devuelven `ENOMEM`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_dupenv_s` busca `varname` en la lista de variables de entorno. Si se encuentra la variable, `_dupenv_s` asigna un búfer y copia el valor de la variable en el búfer. La dirección y la longitud del búfer se devuelven en `buffer` y `numberOfElements`. Mediante la asignación del búfer en sí, `_dupenv_s` proporciona una alternativa más fácil de usar para [getenv_s, _wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md).  
  
> [!NOTE]
>  Es responsabilidad del programa de llamada liberar memoria llamando a [free](../../c-runtime-library/reference/free.md).  
  
 Si no se encuentra la variable, `buffer` se establece en `NULL`, `numberOfElements` se establece en 0 y el valor devuelto es 0, porque esta situación no se considera una condición de error.  
  
 Si el tamaño de búfer no le interesa, puede pasar `NULL` para `numberOfElements`.  
  
 `_dupenv_s` no distingue entre mayúsculas y minúsculas en el sistema operativo Windows. `_dupenv_s` usa la copia del entorno indicado por la variable global `_environ` para tener acceso al entorno. Vea los comentarios de [getenv_s, _wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) para obtener una explicación de `_environ`.  
  
 El valor de `buffer` es una copia del valor de la variable de entorno; su modificación no afecta al entorno. Use la función [_putenv_s, _wputenv_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md) para modificar el valor de una variable de entorno.  
  
 `_wdupenv_s` es una versión con caracteres anchos de `_dupenv_s`; los argumentos de `_wdupenv_s` son cadenas de caracteres anchos. La variable global `_wenviron` es una versión con caracteres anchos de `_environ`. Vea los comentarios de [getenv_s, _wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) para saber más sobre `_wenviron`.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tdupenv_s`|`_dupenv_s`|`_dupenv_s`|`_wdupenv_s`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_dupenv_s`|\<stdlib.h>|  
|`_wdupenv_s`|\<stdlib.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_dupenv_s.c  
#include  <stdlib.h>  
  
int main( void )  
{  
   char *pValue;  
   size_t len;  
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );  
   if ( err ) return -1;  
   printf( "pathext = %s\n", pValue );  
   free( pValue );  
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );  
   if ( err ) return -1;  
   printf( "nonexistentvariable = %s\n", pValue );  
   free( pValue ); // It's OK to call free with NULL  
}  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl  
nonexistentvariable = (null)  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [Constantes de entorno](../../c-runtime-library/environmental-constants.md)   
 [_dupenv_s_dbg, _wdupenv_s_dbg](../../c-runtime-library/reference/dupenv-s-dbg-wdupenv-s-dbg.md)   
 [getenv_s, _wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv_s, _wputenv_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)