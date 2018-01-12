---
title: _matherr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _matherr
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
apitype: DLLExport
f1_keywords:
- _matherr
- matherr
dev_langs: C++
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1c7aa22479630605279b0d1364317d479bd1eac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="matherr"></a>_matherr
Trata errores matemáticos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int _matherr(  
   struct _exception *except   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *except*  
 Puntero a la estructura que contiene información de error.  
  
## <a name="return-value"></a>Valor devuelto  
 **_matherr** devuelve 0 para indicar un error o un valor distinto de cero para indicar que es correcto. Si \_**matherr** devuelve 0, se puede mostrar un mensaje de error y `errno` se establece en un valor de error adecuado. Si \_**matherr** devuelve un valor distinto de cero, no se muestra ningún mensaje de error y `errno` permanece sin cambios.  
  
 Para obtener más información sobre los códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función **_matherr** procesa los errores generados por las funciones de punto flotante de la biblioteca matemática. Estas funciones llaman a \_**matherr** cuando se detecta un error.  
  
 Para llevar a cabo un control de errores especial, puede proporcionar una definición diferente de **_matherr**. Si usa la versión vinculada dinámicamente de la biblioteca en tiempo de ejecución de C (Msvcr90.dll), puede reemplazar la rutina \_**matherr** predeterminada en un ejecutable de cliente por una versión definida por el usuario, pero no puede reemplazar la rutina `_matherr` predeterminada en un cliente DLL de Msvcr90.dll.  
  
 Si se produce un error en una rutina matemática, se llama a **_matherr** con un puntero a una estructura de tipo **_exception** (definida en Math.h) como argumento. La estructura **_exception** contiene los siguientes elementos.  
  
 **int type**  
 Tipo de excepción.  
  
 **char \*name**  
 Nombre de la función en la que se produjo el error.  
  
 **double arg1**, **arg2**  
 Primero y segundo argumento (en caso de existir) para la función.  
  
 **double retval**  
 Valor que devolverá la función.  
  
 **type** especifica el tipo de error matemático. Es uno de los valores siguientes, definidos en Math.h.  
  
 `_DOMAIN`  
 Error de dominio de argumento.  
  
 `_SING`  
 Singularidad de argumento.  
  
 `_OVERFLOW`  
 Error de intervalo de desbordamiento.  
  
 `_PLOSS`  
 Pérdida parcial de significado.  
  
 `_TLOSS`  
 Pérdida total de significado.  
  
 `_UNDERFLOW`  
 El resultado es demasiado pequeño para representarlo (esta condición no se admite actualmente).  
  
 El miembro de estructura **name** es un puntero a una cadena terminada en nulo que contiene el nombre de la función que produjo el error. Los miembros de estructura **arg1** y **arg2** especifican los valores que provocaron el error (si solo se proporciona un argumento, se almacena en **arg1**).  
  
 El valor devuelto predeterminado del valor indicado es **retval**. Si cambia el valor devuelto, se debe especificar si realmente se produjo un error.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_matherr`|\<math.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_matherr.c  
/* illustrates writing an error routine for math   
 * functions. The error function must be:  
 *      _matherr  
 */  
  
#include <math.h>  
#include <string.h>  
#include <stdio.h>  
  
int main()  
{  
    /* Do several math operations that cause errors. The _matherr  
     * routine handles _DOMAIN errors, but lets the system handle  
     * other errors normally.  
     */  
    printf( "log( -2.0 ) = %e\n", log( -2.0 ) );  
    printf( "log10( -5.0 ) = %e\n", log10( -5.0 ) );  
    printf( "log( 0.0 ) = %e\n", log( 0.0 ) );  
}  
  
/* Handle several math errors caused by passing a negative argument  
 * to log or log10 (_DOMAIN errors). When this happens, _matherr  
 * returns the natural or base-10 logarithm of the absolute value  
 * of the argument and suppresses the usual error message.  
 */  
int _matherr( struct _exception *except )  
{  
    /* Handle _DOMAIN errors for log or log10. */  
    if( except->type == _DOMAIN )  
    {  
        if( strcmp( except->name, "log" ) == 0 )  
        {  
            except->retval = log( -(except->arg1) );  
            printf( "Special: using absolute value: %s: _DOMAIN "  
                     "error\n", except->name );  
            return 1;  
        }  
        else if( strcmp( except->name, "log10" ) == 0 )  
        {  
            except->retval = log10( -(except->arg1) );  
            printf( "Special: using absolute value: %s: _DOMAIN "  
                     "error\n", except->name );  
            return 1;  
        }  
    }  
    printf( "Normal: " );  
    return 0;    /* Else use the default actions */  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
Special: using absolute value: log: _DOMAIN error  
log( -2.0 ) = 6.931472e-001  
Special: using absolute value: log10: _DOMAIN error  
log10( -5.0 ) = 6.989700e-001  
Normal: log( 0.0 ) = -1.#INF00e+000  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   