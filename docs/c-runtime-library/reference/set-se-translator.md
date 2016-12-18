---
title: "_set_se_translator | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_se_translator"
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
  - "_set_se_translator"
  - "set_se_translator"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_se_translator (función)"
  - "control de excepciones, cambiar"
  - "set_se_translator (función)"
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_se_translator
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Controla las excepciones Win32 \(excepciones estructuradas de C\) como con excepciones con tipo de C\+\+.  
  
## Sintaxis  
  
```  
_se_translator_function _set_se_translator(  
   _se_translator_function seTransFunction  
);  
```  
  
#### Parámetros  
 `seTransFunction`  
 Puntero a la función estructurada C. el traductor de excepción que escribe.  
  
## Valor devuelto  
 Devuelve un puntero a la función anterior de traductor registrada por `_set_se_translator`, para poder restaurar la función anterior más adelante.  Si no se ha establecido ninguna función anterior, el valor devuelto se puede utilizar para restaurar el comportamiento predeterminado; este valor puede ser NULL.  
  
## Comentarios  
 La función de `_set_se_translator` proporciona una manera de controlar las excepciones Win32 \(excepciones estructuradas C\) como C\+\+ escrito excepciones.  Para permitir a cada excepción de C es administrada por el controlador de c\+\+. `catch` , primero define la clase contenedora de la excepción de C\/C\+\+. desde la que puede utilizar, o derivarse, el atributo una clase concreta escrita a la excepción de C\/C\+\+.  Para utilizar esta clase, instale una función personalizada del traductor de excepción de C denominada por la excepción interna de C\/C\+\+. el mecanismo de control de excepciones se provoca cada vez.  Dentro de la función traductor, puede producir cualquier excepción de tipo se puede detectar mediante un controlador coincidente de C\+\+ `catch` .  
  
 Debe utilizar [\/EHa](../../build/reference/eh-exception-handling-model.md) al utilizar `_set_se_translator`.  
  
 Para especificar una función personalizada de traducción, llame a `_set_se_translator` con el nombre de la función de traducción como argumento.  La función de traductor que se escribe llama una vez para cada invocación de función en la pila que tiene bloques de `try` .  No hay ninguna función predeterminada del traductor.  
  
 La función de traductor debe hacer no más que la excepción tipo \+\+ de C\/C\+\+.  Si hace nada además de producir \(como escribir en un archivo de registro, por ejemplo\) el programa podría comportarse como se espera, porque el número de veces que se llama a la función de traductor es plataforma\- dependiente.  
  
 En un entorno multiproceso, las funciones de traductor se mantienen por separado para cada subproceso.  Cada nuevo subproceso necesita instalar su propia función de traductor.  Así, cada subproceso está responsable de su propia administración de traducción.  `_set_se_translator` es específico de un subproceso; otra DLL puede instalar otra función de traducción.  
  
 La función de `seTransFunction` que se escriba debe ser una función natural\- compilada \(no compilada con \/clr\).  Debe contener un entero sin signo y un puntero a una estructura de Win32 `_EXCEPTION_POINTERS` como argumentos.  Los argumentos son los valores devueltos de llamadas a la API Win32 `GetExceptionCode` y `GetExceptionInformation` funciona, respectivamente.  
  
```  
typedef void (*_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );  
```  
  
 Para `_set_se_translator`, hay implicaciones al vincular dinámicamente a CRT; otra DLL en el proceso puede llamar a `_set_se_translator` y reemplazar el controlador con el suyo.  
  
 Al utilizar `_set_se_translator` de código administrado \(código compilado con \/clr\) o nativo nativo y código administrado, tenga en cuenta que el traductor afecta a las excepciones generadas en código nativo únicamente.  Ninguna excepción administrada generada en código administrado \(por ejemplo al activar `System::Exception`\) no se distribuyen con la función de traductor.  Las excepciones producidas en código administrado mediante la función `RaiseException` Win32 o producidas por una excepción del sistema como una división por la excepción cero se enrutan a través del traductor.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_set_se_translator`|\<eh.h\>|  
  
 La funcionalidad proporcionada por `_set_se_translator` no está disponible en el código compilado con la opción del compilador [\/clr: puro](../../build/reference/clr-common-language-runtime-compilation.md) .  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
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
  
  **En trans\_func.**  
**En finally.**  
**Se detectó una excepción \_\_try con SE\_Exception.**   
## Ejemplo  
 Aunque la funcionalidad proporcionada por `_set_se_translator` no está disponible en código administrado, es posible utilizar esta asignación en código nativo, aunque dicho código nativo está en una compilación en modificador `/clr` , mientras el código nativo se indica mediante `#pragma unmanaged`.  Si una excepción estructurada se está iniciando en el código administrado que se debe asignar, el código que genera y los controla la excepción se deben marcar con `pragma`.  El código siguiente muestra un posible uso.  Para obtener más información, vea [Directives pragma y la palabra clave \_\_pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).  
  
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
  
  **Traducir el control estructurado de excepciones a la excepción de c\+\+.**  
**CMyException detectados.**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)   
 [set\_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set\_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)