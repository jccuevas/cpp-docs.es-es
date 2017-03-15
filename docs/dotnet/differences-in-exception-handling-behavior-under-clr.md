---
title: "Diferencias en el comportamiento del control de excepciones en /CLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXCEPTION_CONTINUE_EXECUTION (macro)"
  - "set_se_translator (función)"
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# Diferencias en el comportamiento del control de excepciones en /CLR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[Conceptos básicos al utilizar controlados Excepciones](../dotnet/basic-concepts-in-using-managed-exceptions.md) trata el control de excepciones en las aplicaciones administradas.  En este tema, las diferencias de comportamiento estándar del control de excepciones y algunas restricciones se describen en detalle.  Para obtener más información, vea [La función de \_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md).  
  
##  <a name="vcconjumpingoutofafinallyblock"></a> El código de un bloque Finally  
 En el código de C\/C\+\+ nativo, el saltar fuera de un bloque de**finally** mediante el control de excepciones estructurado \(SEH\) se permite aunque genere una advertencia.  En [\/clr](../build/reference/clr-common-language-runtime-compilation.md), el saltar fuera de un bloque de **finally** produce un error:  
  
```  
// clr_exception_handling_4.cpp  
// compile with: /clr  
int main() {  
   try {}  
   finally {  
      return 0;   // also fails with goto, break, continue  
    }  
}   // C3276  
```  
  
##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a> Iniciando Excepciones En un filtro de Excepciones  
 Cuando se genera una excepción durante el procesamiento de [filtro de excepción](../cpp/writing-an-exception-filter.md) dentro del código administrado, se detecta y se tratan la excepción como si el filtro devuelve 0.  
  
 Se establece aquí es en contraposición al comportamiento en código nativo donde se produce una excepción anidada, el campo de **ExceptionRecord** en la estructura de **EXCEPTION\_RECORD** \(si devuelve por [GetExceptionInformation](http://msdn.microsoft.com/library/windows/desktop/ms679357)\), y los conjuntos de campos de **ExceptionFlags** el bit 0x10.  El ejemplo siguiente se muestra esta diferencia de comportamiento:  
  
```  
// clr_exception_handling_5.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <assert.h>  
  
#ifndef false  
#define false 0  
#endif  
  
int *p;  
  
int filter(PEXCEPTION_POINTERS ExceptionPointers) {  
   PEXCEPTION_RECORD ExceptionRecord =   
                     ExceptionPointers->ExceptionRecord;  
  
   if ((ExceptionRecord->ExceptionFlags & 0x10) == 0) {  
      // not a nested exception, throw one  
      *p = 0; // throw another AV  
   }  
   else {  
      printf("Caught a nested exception\n");  
      return 1;  
    }  
  
   assert(false);  
  
   return 0;  
}  
  
void f(void) {  
   __try {  
      *p = 0;   // throw an AV  
   }  
   __except(filter(GetExceptionInformation())) {  
      printf_s("We should execute this handler if "  
                 "compiled to native\n");  
    }  
}  
  
int main() {  
   __try {  
      f();  
   }  
   __except(1) {  
      printf_s("The handler in main caught the "  
               "exception\n");  
    }  
}  
```  
  
### Resultados  
  
```  
Caught a nested exception  
We should execute this handler if compiled to native  
```  
  
##  <a name="vccondisassociatedrethrows"></a> Vuelve desasociado  
 **\/clr** no admite de vuelva a iniciar una excepción fuera de un controlador catch \(conocido como rethrow desasociado\).  Las excepciones de este tipo se tratan como rethrow estándar de C\+\+.  Si se encuentra un reinicio desasociado cuando hay una excepción administrada activo, la excepción se encapsula como la excepción y después vuelve de c\+\+.  Las excepciones de este tipo se pueden detectar solo como excepción de [System::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx)escrito.  
  
 El ejemplo siguiente se muestra un vuelve de excepciones administradas como una excepción de c\+\+.:  
  
```  
// clr_exception_handling_6.cpp  
// compile with: /clr  
using namespace System;  
#include <assert.h>  
#include <stdio.h>  
  
void rethrow( void ) {  
   // This rethrow is a dissasociated rethrow.  
   // The exception would be masked as SEHException.  
   throw;  
}  
  
int main() {  
   try {  
      try {  
         throw gcnew ApplicationException;  
      }  
      catch ( ApplicationException^ ) {  
         rethrow();  
         // If the call to rethrow() is replaced with  
         // a throw statement within the catch handler,  
         // the rethrow would be a managed rethrow and  
         // the exception type would remain   
         // System::ApplicationException  
      }  
   }  
  
    catch ( ApplicationException^ ) {  
      assert( false );  
  
      // This will not be executed since the exception  
      // will be masked as SEHException.  
    }  
   catch ( Runtime::InteropServices::SEHException^ ) {  
      printf_s("caught an SEH Exception\n" );  
    }  
}  
```  
  
### Resultados  
  
```  
caught an SEH Exception  
```  
  
##  <a name="vcconexceptionfiltersandexception_continue_execution"></a> Filtros de excepción y EXCEPTION\_CONTINUE\_EXECUTION  
 Si un filtro devuelve `EXCEPTION_CONTINUE_EXECUTION` en una aplicación administrada, se trata como si el filtro devolviera `EXCEPTION_CONTINUE_SEARCH`.  Para obtener más información sobre estas constantes, vea [intento\-excepto la instrucción](../cpp/try-except-statement.md).  
  
 El ejemplo siguiente se muestra esta diferencia:  
  
```  
// clr_exception_handling_7.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <assert.h>  
  
int main() {  
   int Counter = 0;  
   __try {  
      __try  {  
         Counter -= 1;  
         RaiseException (0xe0000000|'seh',  
                         0, 0, 0);  
         Counter -= 2;  
      }  
      __except (Counter) {  
         // Counter is negative,  
         // indicating "CONTINUE EXECUTE"  
         Counter -= 1;  
      }  
    }  
    __except(1) {  
      Counter -= 100;  
   }  
  
   printf_s("Counter=%d\n", Counter);  
}  
```  
  
### Resultados  
  
```  
Counter=-3  
```  
  
##  <a name="vcconthe_set_se_translatorfunction"></a> La función de \_set\_se\_translator  
 La función de traductor, establecido por una llamada a `_set_se_translator`, afecta sólo a las capturas de código no administrado.  El ejemplo siguiente muestra esta limitación:  
  
```  
// clr_exception_handling_8.cpp  
// compile with: /clr /EHa  
#include <iostream>  
#include <windows.h>  
#include <eh.h>  
#pragma warning (disable: 4101)  
using namespace std;  
using namespace System;  
  
#define MYEXCEPTION_CODE 0xe0000101  
  
class CMyException {  
public:  
   unsigned int m_ErrorCode;  
   EXCEPTION_POINTERS * m_pExp;  
  
   CMyException() : m_ErrorCode( 0 ), m_pExp( NULL ) {}  
  
   CMyException( unsigned int i, EXCEPTION_POINTERS * pExp )  
         : m_ErrorCode( i ), m_pExp( pExp ) {}  
  
   CMyException( CMyException& c ) : m_ErrorCode( c.m_ErrorCode ),  
                                      m_pExp( c.m_pExp ) {}  
  
   friend ostream& operator <<   
                 ( ostream& out, const CMyException& inst ) {  
      return out <<  "CMyException[\n" <<    
             "Error Code: " << inst.m_ErrorCode <<  "]";  
    }  
};  
  
#pragma unmanaged   
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS pExp ) {  
   cout <<  "In my_trans_func.\n";  
   throw CMyException( u, pExp );  
}  
  
#pragma managed   
void managed_func() {  
   try  {  
      RaiseException( MYEXCEPTION_CODE, 0, 0, 0 );  
   }  
   catch ( CMyException x ) {}  
   catch ( ... ) {  
      printf_s("This is invoked since "  
               "_set_se_translator is not "  
               "supported when /clr is used\n" );  
    }  
}  
  
#pragma unmanaged   
void unmanaged_func() {  
   try  {  
      RaiseException( MYEXCEPTION_CODE,   
                      0, 0, 0 );  
   }  
   catch ( CMyException x ) {  
      printf("Caught an SEH exception with "  
             "exception code: %x\n", x.m_ErrorCode );  
    }  
    catch ( ... ) {}  
}  
  
// #pragma managed   
int main( int argc, char ** argv ) {  
   _set_se_translator( my_trans_func );  
  
   // It does not matter whether the translator function  
   // is registered in managed or unmanaged code  
   managed_func();  
   unmanaged_func();  
}  
```  
  
### Resultados  
  
```  
This is invoked since _set_se_translator is not supported when /clr is used  
In my_trans_func.  
Caught an SEH exception with exception code: e0000101  
```  
  
## Vea también  
 [Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)   
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)