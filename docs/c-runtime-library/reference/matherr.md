---
title: "_matherr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_matherr"
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
apitype: "DLLExport"
f1_keywords: 
  - "_matherr"
  - "matherr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_matherr (función)"
  - "matherr (función)"
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _matherr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Controlar errores de matemáticas.  
  
## Sintaxis  
  
```  
  
      int _matherr(  
   struct _exception *except   
);  
```  
  
#### Parámetros  
 *excepto*  
 Puntero a la estructura que contiene información de error.  
  
## Valor devuelto  
 \_**matherr** devuelve 0 para indicar un error o un valor distinto de cero para indicar correctamente.  Si \_**matherr** devuelve 0, un mensaje de error puede mostrar y `errno` se establece en un valor de error adecuado.  Si \_**matherr** devuelve un valor distinto de cero, no se muestra ningún mensaje de error y `errno` permanece sin modificar.  
  
 Para obtener más información sobre los códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist, y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Los errores de procesos de la función de**matherr** de \_generados por las funciones de punto flotante de la librería matemática.  \_**matherr** de llamada de estas funciones cuando se detecta un error.  
  
 Para el control de errores especial, puede proporcionar otra definición de \_**matherr**.  Si utiliza la versión dinámicamente vinculada de la biblioteca en tiempo de ejecución de C \(Msvcr90.dll\), puede reemplazar la rutina predeterminada de**matherr** de \_en un archivo ejecutable cliente con una versión definido por el usuario.  Sin embargo, no puede reemplazar la rutina predeterminada de `_matherr` en un cliente de DLL de Msvcr90.dll.  
  
 Cuando se produce un error en una rutina matemático, \_**matherr** lleva un puntero a una estructura del tipo de **\_exception** \(definida en Math.h\) como argumento.  La estructura de **\_exception** contiene los elementos siguientes.  
  
 **int type**  
 Tipo de excepción.  
  
 **char \*name**  
 Nombre de la función donde se produjo el error.  
  
 **double arg1**, **arg2**  
 Primero y segundo \(si existe\) argumentos de la función.  
  
 **double retval**  
 Valor que se devolverá por la función.  
  
 **type** Especifica el tipo de error de matemáticas.  Es uno de los valores siguientes, definidos en Math.h.  
  
 `_DOMAIN`  
 Error de dominio de argumentos.  
  
 `_SING`  
 Singularidad de argumento.  
  
 `_OVERFLOW`  
 Error de intérvalo de capacidad máxima.  
  
 `_PLOSS`  
 Pérdida de significado parcial.  
  
 `_TLOSS`  
 Pérdida total de significado.  
  
 `_UNDERFLOW`  
 El resultado es demasiado pequeño para ser representado. \(Esta condición no se admite actualmente.\)  
  
 El miembro de estructura **name** es un puntero a una cadena terminada en null que contiene el nombre de la función que produjo el error.  Los miembros de la estructura **arg1** y **arg2** especifican valores que produjo el error. \(Si solo se proporciona un argumento, se almacena en **arg1**.\)  
  
 El valor devuelto predeterminado para el error especificado es **retval**.  Si cambia el valor devuelto, debe especificar si se ha producido un error realmente.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_matherr`|\<math.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
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
  
## Resultados  
  
```  
Special: using absolute value: log: _DOMAIN error  
log( -2.0 ) = 6.931472e-001  
Special: using absolute value: log10: _DOMAIN error  
log10( -5.0 ) = 6.989700e-001  
Normal: log( 0.0 ) = -1.#INF00e+000  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Long double](../../misc/long-double.md)