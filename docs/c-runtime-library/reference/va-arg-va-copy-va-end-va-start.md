---
title: "va_arg, va_copy, va_end, va_start | Microsoft Docs"
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
  - "va_arg"
  - "va_end"
  - "va_copy"
  - "va_start"
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
  - "va_arg"
  - "va_start"
  - "va_list"
  - "va_alist"
  - "va_dcl"
  - "va_copy"
  - "va_end"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "listas de argumentos variables, obtener acceso a"
  - "va_start (macro)"
  - "va_arg (macro)"
  - "va_end (macro)"
  - "argumentos [C++], listas de argumentos"
  - "va_list (macro)"
  - "va_dcl (macro)"
  - "va_alist (macro)"
  - "va_copy (macro)"
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# va_arg, va_copy, va_end, va_start
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene acceso a listas de argumentos de variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      type va_arg(  
   va_list arg_ptr,  
   type   
);void va_copy(  
   va_list dest,  
   va_list src  
); // (ISO C99 and later)  
void va_end(  
   va_list arg_ptr   
);  
void va_start(  
   va_list arg_ptr,  
   prev_param   
); // (ANSI C89 and later)  
void va_start(  
   arg_ptr   
);  // (Pre-ANSI C89 standardization version)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 Tipo de argumento que se va a recuperar.  
  
 `arg_ptr`  
 Puntero a la lista de argumentos.  
  
 `dest`  
 Puntero a la lista de argumentos que se van a inicializar desde `src`  
  
 `src`  
 Puntero a la lista de argumentos inicializada que se va a copiar en `dest`.  
  
 `prev_param`  
 Parámetro que precede al primer argumento opcional.  
  
## <a name="return-value"></a>Valor devuelto  
 `va_arg` devuelve el argumento actual. `va_copy`, `va_start` y `va_end` no devuelven valores.  
  
## <a name="remarks"></a>Comentarios  
 Las macros `va_arg`, `va_copy`, `va_end` y `va_start` proporcionan una manera portable de obtener acceso a los argumentos de una función cuando la función toma un número variable de argumentos. Hay dos versiones de las macros. Las macros definidas en STDARG.H cumplen el estándar ISO C99. Las definidas en VARARGS.H se han dejado de utilizar, pero se conservan por razones de compatibilidad con el código escrito antes del estándar ANSI C89.  
  
 Estas macros suponen que la función toma un número fijo de argumentos necesarios, seguido por un número variable de argumentos opcionales. Los argumentos necesarios se declaran como parámetros ordinarios de la función; se puede obtener acceso a ellos con los nombres de parámetro. El acceso a los argumentos opcionales se obtiene a través de las macros de STDARG.H (o VARARGS.H para el código escrito antes del estándar ANSI C89), que establece un puntero al primer argumento opcional de la lista de argumentos, recupera argumentos de la lista y restablece el puntero cuando se finaliza el procesamiento del argumento.  
  
 Las macros estándar de C, definidas en STDARG.H, se utilizan como se indica a continuación:  
  
-   `va_start` establece `arg_ptr` en el primer argumento opcional de la lista de argumentos que se pasa a la función. El argumento `arg_ptr` debe tener el tipo `va_list`. El argumento `prev_param` es el nombre del parámetro necesario inmediatamente anterior al primer argumento opcional de la lista de argumentos. Si `prev_param` se declara con la clase de almacenamiento de registro, el comportamiento de la macro es indefinido. Es necesario usar `va_start` antes de usar `va_arg` por primera vez.  
  
-   `va_arg` recupera un valor de `type` de la ubicación determinada por `arg_ptr`, y aumenta `arg_ptr` para señalar al argumento siguiente de la lista usando el tamaño de `type` para determinar donde empieza el argumento siguiente. `va_arg` se puede usar un número ilimitado de veces en la función para recuperar argumentos de la lista.  
  
-   `va_copy` realiza una copia de una lista de argumentos en su estado actual. El parámetro de `src` debe estar ya inicializado con `va_start`; puede haberse actualizado con llamadas de `va_arg`, pero no puede haberse restablecido con `va_end`. El siguiente argumento recuperado por `va_arg` de `dest` es el mismo que el siguiente argumento se recupera de `src`.  
  
-   Una vez recuperados todos los argumentos, `va_end` restablece el puntero en **NULL**. Es necesario llamar a `va_end` en cada lista de argumentos que se inicialice con `va_start` o `va_copy` antes de que la función devuelva su resultado.  
  
> [!NOTE]
>  Las macros de VARARGS.H han dejado de usarse y se conservan solo por compatibilidad con el código escrito antes de la existencia del estándar ANSI C89. En todos los demás casos, se deben usar las macros de STDARGS.H.  
  
 Cuando se compila utilizando [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), programas que utilizan estas macros pueden generar resultados inesperados debido a las diferencias entre los sistemas de tipos nativos y common language runtime (CLR). Observe este programa:  
  
```  
#include <stdio.h>  
#include <stdarg.h>  
  
void testit (int i, ...)  
{  
    va_list argptr;  
    va_start(argptr, i);  
  
    if (i == 0)  
    {  
        int n = va_arg(argptr, int);  
        printf("%d\n", n);  
    }  
    else  
    {  
        char *s = va_arg(argptr, char*);  
        printf("%s\n", s);  
    }  
}  
  
int main()  
{  
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int  
    testit(1, NULL);       // 2nd problem: NULL is not a char*  
}  
```  
  
 `testit` espera que su segundo parámetro sea un valor `int` o `char*`. Los argumentos que se pasan son 0xffffffff (un valor `unsigned int`, no un valor `int`) y `NULL` (en realidad, un valor `int`, no un valor `char*`). Cuando el programa se compila para código nativo, genera este resultado:  
  
```Output  
-1  
  
(null)  
```  
  
 Sin embargo, cuando se compila el programa mediante el uso de **/clr: pure**, las diferencias de tipo hacen que genere una excepción. La solución es utilizar conversiones explícitas:  
  
```  
int main()  
{  
   testit( 0, (int)0xFFFFFFFF ); // cast unsigned to int  
   testit( 1, (char*)NULL );     // cast int to char*  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< stdio.h > y \< stdarg.h >  
  
 **Encabezado en desuso:** \< varargs.h >  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de la [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_va.c  
/* Compile with: cl /W3 /Tc crt_va.c  
 * The program below illustrates passing a variable  
 * number of arguments using the following macros:  
 *      va_start            va_arg              va_copy  
 *      va_end              va_list  
 */  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <math.h>  
  
double deviation(int first, ...);  
  
int main( void )  
{  
    /* Call with 3 integers (-1 is used as terminator). */  
    printf("Deviation is: %f\n", deviation(2, 3, 4, -1 ));  
  
    /* Call with 4 integers. */  
    printf("Deviation is: %f\n", deviation(5, 7, 9, 11, -1));  
  
    /* Call with just -1 terminator. */  
    printf("Deviation is: %f\n", deviation(-1));  
}  
  
/* Returns the standard deviation of a variable list of integers. */  
double deviation(int first, ...)  
{  
    int count = 0, i = first;  
    double mean = 0.0, sum = 0.0;  
    va_list marker;  
    va_list copy;  
  
    va_start(marker, first);     /* Initialize variable arguments. */  
    va_copy(copy, marker);       /* Copy list for the second pass */  
    while (i != -1)  
    {  
        sum += i;  
        count++;  
        i = va_arg(marker, int);  
    }  
    va_end(marker);              /* Reset variable argument list. */  
    mean = sum ? (sum / count) : 0.0;  
  
    i = first;                  /* reset to calculate deviation */  
    sum = 0.0;  
    while (i != -1)  
    {  
        sum += (i - mean)*(i - mean);  
        i = va_arg(copy, int);  
    }  
    va_end(copy);               /* Reset copy of argument list. */  
    return count ? sqrt(sum / count) : 0.0;  
}  
  
```  
  
## <a name="output"></a>Salida  
  
```Output  
Deviation is: 0.816497  
Deviation is: 2.236068  
Deviation is: 0.000000  
  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 [Clase System::ParamArrayAttribute](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)  
  
## <a name="see-also"></a>Vea también  
 [Acceso a argumentos](../../c-runtime-library/argument-access.md)   
 [vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)