---
title: _set_se_translator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_se_translator
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
- _set_se_translator
- set_se_translator
dev_langs:
- C++
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35ceedca9d26b92d96a3796a3deadee5e62f7f02
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="setsetranslator"></a>_set_se_translator
Controla las excepciones Win32 (excepciones estructuradas de C) como con excepciones con tipo de C++.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_se_translator_function _set_se_translator(  
   _se_translator_function seTransFunction  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `seTransFunction`  
 Puntero a una función de traductor de excepciones estructuradas de C que se escriba.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la función de traductor anterior registrada por `_set_se_translator` para que después se pueda restaurar dicha función. Si no se ha establecido ninguna función anterior, se puede usar el valor devuelto para restaurar el comportamiento predeterminado; este valor puede ser NULL.  
  
## <a name="remarks"></a>Comentarios  
 La función `_set_se_translator` proporciona una manera para controlar las excepciones Win32 (excepciones estructuradas de C) como excepciones con tipo de C++. Para permitir que cada excepción de C se pueda controlar con un controlador `catch` de C++, primero debe definir una clase contenedora de excepciones de C que se pueda usar (o de la que se pueda derivar) con el objetivo de atribuir un tipo de clase específico a una excepción de C. Para usar esta clase, instale una función de traductor de excepciones de C a la que llama el mecanismo de control de excepciones internas cada vez que se produce una excepción de C. Dentro de la función de traductor puede producir cualquier excepción con tipo que se pueda detectar con un controlador `catch` de C++ que coincida.  
  
 Debe usar [/EHa](../../build/reference/eh-exception-handling-model.md) al usar `_set_se_translator`.  
  
 Para especificar una función de traducción personalizada, llame a `_set_se_translator` con el nombre de la función de traducción como argumento. La función de traductor que escriba se llama una vez para cada invocación de función en la pila que tenga bloques `try`. No hay ninguna función de traductor predeterminada.  
  
 La función de traductor solo debe generar una excepción con tipo de C++. Si hace algo más que eso (por ejemplo, escribir en un archivo de registro), es posible que el programa no funcione según lo esperado, ya que la cantidad de veces que se invoca a la función de traductor depende de la plataforma.  
  
 En un entorno multiproceso, las funciones de traductor se mantienen por separado para cada subproceso. Cada subproceso nuevo debe instalar su propia función de traductor. Por lo tanto, cada subproceso se encarga de su propio control de traducción. `_set_se_translator` es específico de un subproceso; otro archivo DLL puede instalar una función de traducción diferente.  
  
 La función `seTransFunction` que escriba debe ser una función compilada de forma nativa (no compilada con/clr). Debe tomar un entero sin signo y un puntero a la estructura `_EXCEPTION_POINTERS` de Win32 como argumentos. Los argumentos son los valores devueltos de las llamadas a las funciones `GetExceptionCode` y `GetExceptionInformation` de la API Win32, respectivamente.  
  
```  
typedef void (*_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );  
```  
  
 Para `_set_se_translator`, hay implicaciones a la hora de vincularse dinámicamente a CRT; otro archivo DLL del proceso podría llamar a `_set_se_translator` y reemplazar el controlador por el suyo propio.  
  
 Si usa `_set_se_translator` desde el código administrado (código compilado con/clr) o desde un código nativo y administrado combinados, tenga en cuenta que el traductor solo afecta a las excepciones generadas en el código nativo. Ninguna excepción administrada que se haya generado en el código administrado (por ejemplo, cuando se genera `System::Exception`) se enruta a través de la función de traductor. Las excepciones generadas en el código administrado mediante la función `RaiseException` de Win32 o producidas por una excepción del sistema (como una excepción de división por cero) se enrutan a través del traductor.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_set_se_translator`|\<eh.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_settrans.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <windows.h>  
#include <eh.h>  
  
void SEFunc();  
void trans_func( unsigned int, EXCEPTION_POINTERS* );  
  
class SE_Exception  
{  
private:  
    unsigned int nSE;  
public:  
    SE_Exception() {}  
    SE_Exception( unsigned int n ) : nSE( n ) {}  
    ~SE_Exception() {}  
    unsigned int getSeNumber() { return nSE; }  
};  
int main( void )  
{  
    try  
    {  
        _set_se_translator( trans_func );  
        SEFunc();  
    }  
    catch( SE_Exception e )  
    {  
        printf( "Caught a __try exception with SE_Exception.\n" );  
    }  
}  
void SEFunc()  
{  
    __try  
    {  
        int x, y=0;  
        x = 5 / y;  
    }  
    __finally  
    {  
        printf( "In finally\n" );  
    }  
}  
void trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )  
{  
    printf( "In trans_func.\n" );  
    throw SE_Exception();  
}  
```  
  
```Output  
In trans_func.  
In finally  
Caught a __try exception with SE_Exception.  
```  
  
## <a name="example"></a>Ejemplo  
 Aunque la funcionalidad proporcionada por `_set_se_translator` no está disponible en el código administrado, se puede usar esta asignación en el código nativo, incluso si dicho código está en una compilación en el modificador `/clr`, siempre y cuando el código nativo se indique mediante `#pragma unmanaged`. Si se genera una excepción estructurada en un código administrado que se debe asignar, el código que genera y controla la excepción se debe marcar con `pragma`. En el siguiente código se muestra un uso posible. Para obtener más información, vea [Directives pragma y la palabra clave __pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).  
  
```  
// crt_set_se_translator_clr.cpp  
// compile with: /clr  
#include <windows.h>  
#include <eh.h>  
#include <assert.h>  
#include <stdio.h>  
  
int thrower_func(int i) {  
   int j = i/0;  
  return 0;  
}  
  
class CMyException{  
};  
  
#pragma unmanaged  
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS pExp )  
{  
printf("Translating the structured exception to a C++"  
             " exception.\n");  
throw CMyException();  
}  
  
void DoTest()  
{  
    try  
    {  
      thrower_func(10);  
    }   
  
    catch(CMyException e)  
    {  
printf("Caught CMyException.\n");  
    }  
    catch(...)  
    {  
      printf("Caught unexpected SEH exception.\n");  
    }  
}  
#pragma managed  
  
int main(int argc, char** argv) {  
    _set_se_translator(my_trans_func);  
    DoTest();  
    return 0;  
}  
```  
  
```Output  
Translating the structured exception to a C++ exception.  
Caught CMyException.  
```  
  
## <a name="see-also"></a>Vea también  
 [Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)   
 [set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)