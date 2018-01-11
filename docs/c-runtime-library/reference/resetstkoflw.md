---
title: _resetstkoflw | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _resetstkoflw
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
- resetstkoflw
- _resetstkoflw
dev_langs: C++
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5bebef156656ba3618c216ad8266e1baf5dd7f9b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resetstkoflw"></a>_resetstkoflw
Se recupera de un desbordamiento de pila.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int _resetstkoflw ( void );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Valor distinto de cero si la función se ejecuta correctamente, cero si se produce un error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_resetstkoflw` se recupera de una condición del desbordamiento de pila, lo que permite que el continúe en lugar de generar un error de excepción grave. Si no se llama a la función `_resetstkoflw`, no queda ninguna página de protección después de la excepción anterior. La próxima vez que haya un desbordamiento de pila, no habrá ninguna excepción en absoluto y el proceso finalizará sin avisar.  
  
 Si un subproceso de una aplicación provoca una excepción **EXCEPTION_STACK_OVERFLOW**, el subproceso ha dejado la pila en estado dañado. Este caso es distinto de los de otras excepciones como **EXCEPTION_ACCESS_VIOLATION** o **EXCEPTION_INT_DIVIDE_BY_ZERO**, en los que la pila no está dañada. La pila se establece de forma arbitraria en un valor pequeño la primera vez que se carga el programa. Después, la pila aumenta de tamaño a petición para satisfacer las necesidades del subproceso. Para que sea así, se pone una página con acceso de PAGE_GUARD al final de la pila actual. Para obtener más información, vea [Creating Guard Pages](http://msdn.microsoft.com/library/windows/desktop/aa366549) (Crear páginas de protección).  
  
 Si el código hace que el puntero de pila señale a una dirección de esta página, se produce una excepción y el sistema realiza las tres operaciones siguientes:  
  
-   Quita la protección de PAGE_GUARD de la página de protección, de modo que el subproceso pueda leer y escribir datos en la memoria.  
  
-   Asigna una nueva página de protección que se ubica una página por detrás de la última.  
  
-   Vuelve a ejecutar la instrucción que provocó la excepción.  
  
 De esta manera, el sistema puede aumentar automáticamente el tamaño de la pila del subproceso. Cada subproceso de un proceso tiene un tamaño de pila máximo. El tamaño de pila se establece en tiempo de compilación mediante [/STACK (Asignaciones de la pila)](../../build/reference/stack-stack-allocations.md) o mediante la instrucción [STACKSIZE](../../build/reference/stacksize.md) del archivo .def del proyecto.  
  
 Cuando se supera este tamaño de pila máximo, el sistema realiza las tres operaciones siguientes:  
  
-   Quite la protección de PAGE_GUARD de la página de protección, como ya se ha descrito.  
  
-   Intenta asignar una nueva página de protección detrás de la última. Sin embargo, se produce un error porque se ha superado el tamaño de pila máximo.  
  
-   Provoca una excepción para que el subproceso pueda controlarla en el bloque de excepciones.  
  
 Observe que, en este punto, la pila ya no tiene una página de protección. La próxima vez que el programa aumente el tamaño de la pila hasta el final, donde debe haber una página de protección, el programa escribe más allá del final de la pila y provoca una infracción de acceso.  
  
 Llame a `_resetstkoflw` para restaurar la página de protección siempre que la recuperación se realice después de una excepción de desbordamiento de pila. Se puede llamar a esta función desde dentro del cuerpo principal de un bloque `__except` o desde fuera de un bloque **__except**. Sin embargo, hay restricciones en cuanto a cuándo se debe usar. Nunca se debe llamar a `_resetstkoflw` desde:  
  
-   Una expresión de filtro.  
  
-   Una función de filtro.  
  
-   Una función a la que se llama desde una función de filtro.  
  
-   Bloque **catch**.  
  
-   Un bloque `__finally`.  
  
 En estos puntos, la pila no está suficientemente desenredada todavía.  
  
 Las excepciones de desbordamiento de pila se generan como excepciones estructuradas, y no excepciones de C++, por lo que `_resetstkoflw` no resulta útil en un bloque **catch** normal, porque no detecta excepciones de desbordamiento de pila. Sin embargo, si se usa [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) para implementar un traductor de excepciones estructuradas que provoca excepciones de C++ (como en el segundo ejemplo), una excepción de desbordamiento de pila da lugar a una excepción de C++ que un bloque catch de C++ puede controlar.  
  
 No es seguro llamar a **_resetstkoflw** en un bloque catch de C++ al que se llega desde una excepción provocada por la función del traductor de excepciones estructuradas. En ese caso, no se libera espacio de pila y el puntero de pila no se restablece hasta que está fuera del bloque catch, aunque se haya llamado a destructores para todos los objetos que se puedan destruir antes del bloque catch. No se debe llamar a esta función hasta que se libere espacio en la pila y se haya restablecido el puntero de la pila. Por consiguiente, solo se debe llamar después de salir del bloque catch. En el bloque catch se debe usar el menor espacio de pila posible, porque un desbordamiento de pila que tenga lugar en el bloque catch que está tratando de recuperarse de un desbordamiento de pila anterior no es recuperable, y podría hacer que el programa dejara de responder porque el desbordamiento en el bloque catch desencadena una excepción controlada por el mismo bloque catch.  
  
 Hay situaciones en las que **_resetstkoflw** puede producir un error aunque se use en una ubicación adecuada (por ejemplo, en un bloque **__except**). Si, incluso después de desenredar la pila, no queda suficiente espacio de pila para ejecutar **_resetstkoflw** sin escribir en la última página de la pila, **_resetstkoflw** no puede restablecer la última página de pila como página de protección y devuelve 0, que indica error. Por consiguiente, para que el uso de esta función sea seguro se debe comprobar el valor devuelto en lugar de suponer que la pila es seguro y se puede usar.  
  
 Control estructurado de excepciones no detectará un `STATUS_STACK_OVERFLOW` excepción cuando la aplicación se compila con `/clr` (consulte [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_resetstkoflw`|\<malloc.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
 **Bibliotecas:** todas las versiones de las [características de la biblioteca de CRT](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso recomendado de la función `_resetstkoflw`.  
  
```  
// crt_resetstkoflw.c  
// Launch program with and without arguments to observe  
// the difference made by calling _resetstkoflw.  
  
#include <malloc.h>  
#include <stdio.h>  
#include <windows.h>  
  
void recursive(int recurse)  
{  
   _alloca(2000);  
   if (recurse)  
      recursive(recurse);  
}  
  
// Filter for the stack overflow exception.  
// This function traps the stack overflow exception, but passes  
// all other exceptions through.   
int stack_overflow_exception_filter(int exception_code)  
{  
   if (exception_code == EXCEPTION_STACK_OVERFLOW)  
   {  
       // Do not call _resetstkoflw here, because  
       // at this point, the stack is not yet unwound.  
       // Instead, signal that the handler (the __except block)  
       // is to be executed.  
       return EXCEPTION_EXECUTE_HANDLER;  
   }  
   else  
       return EXCEPTION_CONTINUE_SEARCH;  
}  
  
int main(int ac)  
{  
   int i = 0;  
   int recurse = 1, result = 0;  
  
   for (i = 0 ; i < 10 ; i++)  
   {  
      printf("loop #%d\n", i + 1);  
      __try  
      {  
         recursive(recurse);  
  
      }  
  
      __except(stack_overflow_exception_filter(GetExceptionCode()))  
      {  
         // Here, it is safe to reset the stack.  
  
         if (ac >= 2)  
         {  
            puts("resetting stack overflow");  
            result = _resetstkoflw();  
         }  
      }  
  
      // Terminate if _resetstkoflw failed (returned 0)  
      if (!result)  
         return 3;  
   }  
  
   return 0;  
}  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
 Sin argumentos de programa:  
  
```  
loop #1  
```  
  
 El programa deja de responder sin ejecutar otras iteraciones.  
  
 Con argumentos de programa:  
  
```  
loop #1  
resetting stack overflow  
loop #2  
resetting stack overflow  
loop #3  
resetting stack overflow  
loop #4  
resetting stack overflow  
loop #5  
resetting stack overflow  
loop #6  
resetting stack overflow  
loop #7  
resetting stack overflow  
loop #8  
resetting stack overflow  
loop #9  
resetting stack overflow  
loop #10  
resetting stack overflow  
```  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra el uso recomendado de `_resetstkoflw` en un programa en el que las excepciones estructuradas se convierten en excepciones de C++.  
  
### <a name="code"></a>Código  
  
```  
// crt_resetstkoflw2.cpp  
// compile with: /EHa  
// _set_se_translator requires the use of /EHa  
#include <malloc.h>  
#include <stdio.h>  
#include <windows.h>  
#include <eh.h>  
  
class Exception { };  
  
class StackOverflowException : Exception { };  
  
// Because the overflow is deliberate, disable the warning that  
// this function will cause a stack overflow.  
#pragma warning (disable: 4717)  
void CauseStackOverflow (int i)  
{  
        // Overflow the stack by allocating a large stack-based array  
        // in a recursive function.  
        int a[10000];  
        printf("%d ", i);  
        CauseStackOverflow (i + 1);  
}  
  
void __cdecl SEHTranslator (unsigned int code, _EXCEPTION_POINTERS*)  
{  
   // For stack overflow exceptions, throw our own C++   
   // exception object.  
   // For all other exceptions, throw a generic exception object.  
   // Use minimal stack space in this function.  
   // Do not call _resetstkoflw in this function.  
  
   if (code == EXCEPTION_STACK_OVERFLOW)  
      throw StackOverflowException ( );  
   else  
      throw Exception( );  
}  
  
int main ( )  
{  
        bool stack_reset = false;  
        bool result = false;  
  
        // Set up a function to handle all structured exceptions,  
        // including stack overflow exceptions.  
        _set_se_translator (SEHTranslator);  
  
        try  
        {  
            CauseStackOverflow (0);  
        }  
        catch (StackOverflowException except)  
        {  
                // Use minimal stack space here.  
                // Do not call _resetstkoflw here.  
                printf("\nStack overflow!\n");  
                stack_reset = true;  
        }  
        catch (Exception except)  
        {  
                // Do not call _resetstkoflw here.  
                printf("\nUnknown Exception!\n");  
        }  
        if (stack_reset)  
        {  
          result = _resetstkoflw();  
          // If stack reset failed, terminate the application.  
          if (result == 0)  
             exit(1);  
        }  
  
        void* pv = _alloca(100000);  
        printf("Recovered from stack overflow and allocated 100,000 bytes"  
               " using _alloca.");  
  
   return 0;  
}  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24  
Stack overflow!  
Recovered from stack overflow and allocated 100,000 bytes using _alloca.  
```  
  
## <a name="see-also"></a>Vea también  
 [_alloca](../../c-runtime-library/reference/alloca.md)