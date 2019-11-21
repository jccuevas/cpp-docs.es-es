---
title: Transportar excepciones entre subprocesos
ms.date: 05/07/2019
helpviewer_keywords:
- std::current_exception
- transporting exceptions between threads
- std::copy_exception
- exception_ptr
- std::exception_ptr
- std::rethrow_exception
- current_exception
- transport exceptions between threads
- copy_exception
- rethrow_exception
- move exceptions between threads
ms.assetid: 5c95d57b-acf5-491f-8122-57c5df0edd98
ms.openlocfilehash: 25b09c508b932a4d1470f6b23f03aa52e62c68cc
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246312"
---
# <a name="transporting-exceptions-between-threads"></a>Transportar excepciones entre subprocesos

The Microsoft C++ compiler (MSVC) supports *transporting an exception* from one thread to another. El transporte de excepciones permite detectar una excepción en un subproceso y hacer que parezca que la excepción se produce en un subproceso diferente. Por ejemplo, esta característica se puede utilizar para escribir una aplicación multiproceso en la que el subproceso principal controla todas las excepciones producidas por sus subprocesos secundarios. El transporte de excepciones es útil principalmente para los desarrolladores que crean bibliotecas de programación o sistemas paralelos. To implement transporting exceptions, MSVC provides the [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) type and the [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception), and [make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) functions.

## <a name="syntax"></a>Sintaxis

```cpp
namespace std
{
   typedef unspecified exception_ptr;
   exception_ptr current_exception();
   void rethrow_exception(exception_ptr p);
   template<class E>
       exception_ptr make_exception_ptr(E e) noexcept;
}
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*unspecified*|Clase interna sin especificar que se utiliza para implementar el tipo `exception_ptr`.|
|*p*|Objeto `exception_ptr` que hace referencia a una excepción.|
|*E*|Clase que representa una excepción.|
|*e*|Instancia de la clase del parámetro `E`.|

## <a name="return-value"></a>Valor devuelto

La función `current_exception` devuelve un objeto `exception_ptr` que hace referencia a la excepción que está en curso actualmente. Si no hay ninguna excepción en curso, la función devuelve un objeto `exception_ptr` que no está asociado a ninguna excepción.

The `make_exception_ptr` function returns an `exception_ptr` object that references the exception specified by the *e* parameter.

## <a name="remarks"></a>Comentarios

### <a name="scenario"></a>Escenario

Suponga que desea crear una aplicación que se pueda escalar para controlar una cantidad de trabajo variable. Para lograr este objetivo, diseña una aplicación multiproceso en la que un subproceso principal inicial crea tantos subprocesos secundarios como necesita para hacer el trabajo. Los subprocesos secundarios ayudan al subproceso principal a administrar los recursos, equilibrar las cargas y mejorar el rendimiento. Al distribuir el trabajo, la aplicación multiproceso funciona mejor que una aplicación uniproceso.

Sin embargo, si un subproceso secundario produce una excepción, subproceso principal debe controlarla. Esto es porque desea que la aplicación controle las excepciones de una manera coherente y unificada independientemente del número de subprocesos secundarios.

### <a name="solution"></a>Soluciones

Para controlar el escenario anterior, el estándar de C++ admite transportar una excepción entre subprocesos. If a secondary thread throws an exception, that exception becomes the *current exception*. By analogy to the real world, the current exception is said to be *in flight*. La excepción actual está en vuelo desde el momento en que se produce hasta que el controlador de excepciones que la captura vuelve.

The secondary thread can catch the current exception in a **catch** block, and then call the `current_exception` function to store the exception in an `exception_ptr` object. El objeto `exception_ptr` debe estar disponible para el subproceso secundario y para el subproceso principal. Por ejemplo, el objeto `exception_ptr` puede ser una variable global cuyo acceso esté controlado mediante una exclusión mutua. The term *transport an exception* means an exception in one thread can be converted to a form that can be accessed by another thread.

A continuación, el subproceso principal llama a la función `rethrow_exception`, que extrae y produce la excepción desde el objeto `exception_ptr`. Cuando se produce la excepción, se convierte en la excepción actual del subproceso principal. Es decir, parece que la excepción procede del subproceso principal.

Finally, the primary thread can catch the current exception in a **catch** block and then process it or throw it to a higher level exception handler. O bien, el subproceso principal puede omitir la excepción y permitir que el proceso finalice.

La mayoría de las aplicaciones no tienen que transportar excepciones entre subprocesos. Sin embargo, esta característica es útil en un sistema informático en paralelo porque el sistema puede repartir el trabajo entre los subprocesos secundarios, los procesadores o los núcleos. En un entorno informático en paralelo, un único subproceso dedicado puede controlar todas las excepciones de los subprocesos secundarios y puede presentar un modelo coherente de control de excepciones a cualquier aplicación.

Para obtener más información sobre la propuesta del comité de normas de C++, busque en Internet el número de documento N2179, titulado "Language Support for Transporting Exceptions between Threads" (Compatibilidad con lenguajes para transportar excepciones entre subprocesos).

### <a name="exception-handling-models-and-compiler-options"></a>Exception-handling models and compiler options

El modelo de control de excepciones de una aplicación determina si puede detectar y transportar una excepción. Visual C++ admite tres modelos que pueden controlar excepciones de C++, excepciones de Control de excepciones estructurado (SEH) y excepciones de Common Language Runtime (CLR). Use the [/EH](../build/reference/eh-exception-handling-model.md) and [/clr](../build/reference/clr-common-language-runtime-compilation.md) compiler options to specify your application's exception-handling model.

Solo la combinación siguiente de opciones del compilador e instrucciones de programación puede transportar una excepción. Otras combinaciones no pueden detectar excepciones, o pueden detectar pero no pueden transportar excepciones.

- The **/EHa** compiler option and the **catch** statement can transport SEH and C++ exceptions.

- The **/EHa**, **/EHs**, and **/EHsc** compiler options and the **catch** statement can transport C++ exceptions.

- The **/CLR** compiler option and the **catch** statement can transport C++ exceptions. The **/CLR** compiler option implies specification of the **/EHa** option. Tenga en cuenta que el compilador no admite transportar excepciones administradas. This is because managed exceptions, which are derived from the [System.Exception class](../standard-library/exception-class.md), are already objects that you can move between threads by using the facilities of the common languange runtime.

   > [!IMPORTANT]
   > We recommend that you specify the **/EHsc** compiler option and catch only C++ exceptions. You expose yourself to a security threat if you use the **/EHa** or **/CLR** compiler option and a **catch** statement with an ellipsis *exception-declaration* (`catch(...)`). You probably intend to use the **catch** statement to capture a few specific exceptions. Sin embargo, la instrucción `catch(...)` captura todas las excepciones de C++ y SEH, incluidas las inesperadas que deben ser irrecuperables. Si se omite o se controla mal una excepción inesperada, el código malintencionado puede aprovechar esa oportunidad para socavar la seguridad del programa.

## <a name="usage"></a>Uso

The following sections describe how to transport exceptions by using the `exception_ptr` type, and the `current_exception`, `rethrow_exception`, and `make_exception_ptr` functions.

## <a name="exception_ptr-type"></a>exception_ptr type

Utilice un objeto `exception_ptr` para hacer referencia a la excepción actual o a una instancia de una excepción especificada por el usuario. En la implementación de Microsoft, una excepción se representa mediante una estructura [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record). Cada objeto `exception_ptr` incluye un campo de referencia de excepción que apunta a una copia de la estructura `EXCEPTION_RECORD` que representa la excepción.

Cuando se declara una variable `exception_ptr`, la variable no está asociada a ninguna excepción. Es decir, su campo de referencia de excepción es NULL. Este tipo de objeto `exception_ptr` se denomina *exception_ptr null*.

Utilice la función `current_exception` o `make_exception_ptr` para asignar una excepción a un objeto `exception_ptr`. Cuando se asigna una excepción a una variable `exception_ptr`, el campo de referencia de excepción de la variable apunta a una copia de la excepción. Si no hay memoria suficiente para copiar la excepción, el campo de referencia de excepción apunta a una copia de una excepción [std::bad_alloc](../standard-library/bad-alloc-class.md). If the `current_exception` or `make_exception_ptr` function cannot copy the exception for any other reason, the function calls the [terminate](../c-runtime-library/reference/terminate-crt.md) function to exit the current process.

A pesar de su nombre, un objeto `exception_ptr` no es en sí mismo un puntero. It does not obey pointer semantics and cannot be used with the pointer member access (`->`) or indirection (`*`) operators. El objeto `exception_ptr` no tiene ningún miembro de datos ni ninguna función miembro de tipo público.

### <a name="comparisons"></a>Comparaciones

Se pueden usar los operadores de igualdad (`==`) y desigualdad (`!=`) para comparar dos objetos `exception_ptr`. Los operadores no comparan el valor binario (patrón de bits) de las estructuras `EXCEPTION_RECORD` que representan las excepciones. En su lugar, los operadores comparan las indicaciones del campo de referencia de excepción de los objetos `exception_ptr`. Por tanto, un `exception_ptr` NULL y el valor NULL se consideran iguales.

## <a name="current_exception-function"></a>current_exception function

Call the `current_exception` function in a **catch** block. If an exception is in flight and the **catch** block can catch the exception, the `current_exception` function returns an `exception_ptr` object that references the exception. De lo contrario, la función devuelve un objeto `exception_ptr` NULL.

### <a name="details"></a>Detalles

The `current_exception` function captures the exception that is in flight regardless of whether the **catch** statement specifies an [exception-declaration](../cpp/try-throw-and-catch-statements-cpp.md) statement.

The destructor for the current exception is called at the end of the **catch** block if you do not rethrow the exception. En cambio, incluso aunque llame a la función`current_exception` en el destructor, la función devuelve un objeto `exception_ptr` que hace referencia a la excepción actual.

Las llamadas sucesivas a la función `current_exception` devuelven objetos `exception_ptr` que hacen referencia a distintas copias de la excepción actual. Por tanto, al comparar los objetos se consideran diferentes porque hacen referencia a copias distintas, incluso aunque las copias tengan el mismo valor binario.

### <a name="seh-exceptions"></a>SEH exceptions

If you use the **/EHa** compiler option, you can catch an SEH exception in a C++ **catch** block. La función `current_exception` devuelve un objeto `exception_ptr` que hace referencia a la excepción SEH. And the `rethrow_exception` function throws the SEH exception if you call it with thetransported `exception_ptr` object as its argument.

The `current_exception` function returns a null `exception_ptr` if you call it in an SEH **__finally** termination handler, an **__except** exception handler, or the **__except** filter expression.

Una excepción transportada no admite excepciones anidadas. Se genera una excepción anidada si se produce otra excepción mientras se está controlando una excepción. Si se detecta una excepción anidada, el miembro de datos `EXCEPTION_RECORD.ExceptionRecord` apunta a una cadena de estructuras `EXCEPTION_RECORD` que describen las excepciones asociadas. La función `current_exception` no admite excepciones anidadas porque devuelve un objeto `exception_ptr` cuyo miembro de datos `ExceptionRecord` se pone a cero.

Si se detecta una excepción SEH, debe administrar la memoria a la que hace referencia cualquier puntero en la matriz de miembros de datos `EXCEPTION_RECORD.ExceptionInformation`. Debe garantizar que la memoria es válida mientras dura el objeto `exception_ptr` correspondiente y que la memoria se liberará cuando se elimine el objeto `exception_ptr`.

Puede utilizar funciones de traductor de excepciones estructuradas (SE) junto con la característica de transporte de excepciones. Si una excepción SEH se traduce a una excepción de C++, la función `current_exception` devuelve un `exception_ptr` que hace referencia a la excepción traducida en lugar de a la excepción SEH original. La función `rethrow_exception` produce posteriormente la excepción traducida, no la excepción original. For more information about SE translator functions, see [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrow_exception-function"></a>rethrow_exception function

Después de almacenar una excepción detectada en un objeto `exception_ptr`, el subproceso principal puede procesar el objeto. En el subproceso principal, llame a la función `rethrow_exception` junto con el objeto `exception_ptr` como argumento. La función `rethrow_exception` extrae la excepción del objeto `exception_ptr` y después produce la excepción en el contexto del subproceso principal. If the *p* parameter of the `rethrow_exception` function is a null `exception_ptr`, the function throws [std::bad_exception](../standard-library/bad-exception-class.md).

La excepción extraída es ahora la excepción actual en el subproceso principal y puede controlarla como haría con cualquier otra excepción. If you catch the exception, you can handle it immediately or use a **throw** statement to send it to a higher level exception handler. De lo contrario, no haga nada y deje que el controlador de excepciones predeterminado del sistema finalice el proceso.

## <a name="make_exception_ptr-function"></a>make_exception_ptr (Función)

La función `make_exception_ptr` toma una instancia de una clase como argumento y devuelve un `exception_ptr` que hace referencia a la instancia. Normalmente, se especifica un objeto [exception (Clase)](../standard-library/exception-class.md) como argumento para la función `make_exception_ptr`, aunque el argumento puede ser cualquier objeto de clase.

Calling the `make_exception_ptr` function is equivalent to throwing a C++ exception, catching it in a **catch** block, and then calling the `current_exception` function to return an `exception_ptr` object that references the exception. La implementación de Microsoft de la función `make_exception_ptr` es más eficaz que producir y detectar después una excepción.

Una aplicación no suele necesitar la función `make_exception_ptr` y desaconsejamos su uso.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se transporta una excepción estándar de C++ y una excepción personalizada de C++ de un subproceso a otro.

```cpp
// transport_exception.cpp
// compile with: /EHsc /MD
#include <windows.h>
#include <stdio.h>
#include <exception>
#include <stdexcept>

using namespace std;

// Define thread-specific information.
#define THREADCOUNT 2
exception_ptr aException[THREADCOUNT];
int           aArg[THREADCOUNT];

DWORD WINAPI ThrowExceptions( LPVOID );

// Specify a user-defined, custom exception.
// As a best practice, derive your exception
// directly or indirectly from std::exception.
class myException : public std::exception {
};
int main()
{
    HANDLE aThread[THREADCOUNT];
    DWORD ThreadID;

    // Create secondary threads.
    for( int i=0; i < THREADCOUNT; i++ )
    {
        aArg[i] = i;
        aThread[i] = CreateThread(
            NULL,       // Default security attributes.
            0,          // Default stack size.
            (LPTHREAD_START_ROUTINE) ThrowExceptions,
            (LPVOID) &aArg[i], // Thread function argument.
            0,          // Default creation flags.
            &ThreadID); // Receives thread identifier.
        if( aThread[i] == NULL )
        {
            printf("CreateThread error: %d\n", GetLastError());
            return -1;
        }
    }

    // Wait for all threads to terminate.
    WaitForMultipleObjects(THREADCOUNT, aThread, TRUE, INFINITE);
    // Close thread handles.
    for( int i=0; i < THREADCOUNT; i++ ) {
        CloseHandle(aThread[i]);
    }

    // Rethrow and catch the transported exceptions.
    for ( int i = 0; i < THREADCOUNT; i++ ) {
        try {
            if (aException[i] == NULL) {
                printf("exception_ptr %d: No exception was transported.\n", i);
            }
            else {
                rethrow_exception( aException[i] );
            }
        }
        catch( const invalid_argument & ) {
            printf("exception_ptr %d: Caught an invalid_argument exception.\n", i);
        }
        catch( const myException & ) {
            printf("exception_ptr %d: Caught a  myException exception.\n", i);
        }
    }
}
// Each thread throws an exception depending on its thread
// function argument, and then ends.
DWORD WINAPI ThrowExceptions( LPVOID lpParam )
{
    int x = *((int*)lpParam);
    if (x == 0) {
        try {
            // Standard C++ exception.
            // This example explicitly throws invalid_argument exception.
            // In practice, your application performs an operation that
            // implicitly throws an exception.
            throw invalid_argument("A C++ exception.");
        }
        catch ( const invalid_argument & ) {
            aException[x] = current_exception();
        }
    }
    else {
        // User-defined exception.
        aException[x] = make_exception_ptr( myException() );
    }
    return TRUE;
}
```

```Output
exception_ptr 0: Caught an invalid_argument exception.
exception_ptr 1: Caught a  myException exception.
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<exception>

## <a name="see-also"></a>Vea también

[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH (Modelo de control de excepciones)](../build/reference/eh-exception-handling-model.md)<br/>
[/clr (Compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)
