---
title: Diferencias en el comportamiento del control de excepciones en -CLR
ms.date: 11/04/2016
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
ms.openlocfilehash: 940d297ff77248ba9e9980f7032b5d722d95c7eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364372"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>Diferencias en el comportamiento del control de excepciones en /CLR

[Conceptos básicos en el uso de excepciones administradas](../dotnet/basic-concepts-in-using-managed-exceptions.md) describe el control de excepciones en aplicaciones administradas. En este tema, las diferencias con respecto al comportamiento estándar del control de excepciones y algunas restricciones se describen en detalle. Para obtener más información, consulte [La función _set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="jumping-out-of-a-finally-block"></a><a name="vcconjumpingoutofafinallyblock"></a>Saltar de un bloque finally

En el código nativo de C/C++, se permite saltar de un bloque __**finally** mediante el control de excepciones estructurado (SEH), aunque produce una advertencia.  En [/clr](../build/reference/clr-common-language-runtime-compilation.md), saltar de un bloque **finally** produce un error:

```cpp
// clr_exception_handling_4.cpp
// compile with: /clr
int main() {
   try {}
   finally {
      return 0;   // also fails with goto, break, continue
    }
}   // C3276
```

## <a name="raising-exceptions-within-an-exception-filter"></a><a name="vcconraisingexceptionswithinanexceptionfilter"></a>Aumento de excepciones dentro de un filtro de excepciones

Cuando se produce una excepción durante el procesamiento de un filtro de [excepción](../cpp/writing-an-exception-filter.md) dentro del código administrado, la excepción se detecta y se trata como si el filtro devuelve 0.

Esto contrasta con el comportamiento en código nativo donde se genera una excepción anidada, se establece el campo **ExceptionRecord** de la estructura **EXCEPTION_RECORD** (devuelta por [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation)) y el campo **ExceptionFlags** establece el bit 0x10. En el ejemplo siguiente se muestra esta diferencia de comportamiento:

```cpp
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

### <a name="output"></a>Output

```Output
Caught a nested exception
We should execute this handler if compiled to native
```

## <a name="disassociated-rethrows"></a><a name="vccondisassociatedrethrows"></a>Rethrows desasociados

**/clr** no admite volver a producir una excepción fuera de un controlador catch (conocido como un relanzamiento desasociado). Las excepciones de este tipo se tratan como un relanzamiento estándar de C++. Si se encuentra un relanzamiento desasociado cuando hay una excepción administrada activa, la excepción se ajusta como una excepción de C++ y, a continuación, se vuelve a producir. Las excepciones de este tipo solo se <xref:System.Runtime.InteropServices.SEHException>pueden detectar como una excepción de tipo .

En el ejemplo siguiente se muestra una excepción administrada que se vuelve a producir como una excepción C++:

```cpp
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

### <a name="output"></a>Output

```Output
caught an SEH Exception
```

## <a name="exception-filters-and-exception_continue_execution"></a><a name="vcconexceptionfiltersandexception_continue_execution"></a>Filtros de excepción y EXCEPTION_CONTINUE_EXECUTION

Si un `EXCEPTION_CONTINUE_EXECUTION` filtro devuelve en una aplicación administrada, `EXCEPTION_CONTINUE_SEARCH`se trata como si el filtro devolviera . Para obtener más información sobre estas constantes, vea [try-except Statement](../cpp/try-except-statement.md).

En el ejemplo siguiente se muestra esta diferencia:

```cpp
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

### <a name="output"></a>Output

```Output
Counter=-3
```

## <a name="the-_set_se_translator-function"></a><a name="vcconthe_set_se_translatorfunction"></a>La función _set_se_translator

La función de traductor, `_set_se_translator`establecida por una llamada a , solo afecta a las capturas en código no administrado. En el ejemplo siguiente se muestra esta limitación:

```cpp
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

### <a name="output"></a>Output

```Output
This is invoked since _set_se_translator is not supported when /clr is used
In my_trans_func.
Caught an SEH exception with exception code: e0000101
```

## <a name="see-also"></a>Consulte también

[Control de excepciones](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Manejo de Excepciones en MSVC](../cpp/exception-handling-in-visual-cpp.md)
