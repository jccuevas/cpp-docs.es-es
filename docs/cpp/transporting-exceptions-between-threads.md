---
title: "Transportar excepciones entre subprocesos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "std::current_exception"
  - "transportar excepciones entre subprocesos"
  - "std::copy_exception"
  - "exception_ptr"
  - "std::exception_ptr"
  - "std::rethrow_exception"
  - "current_exception"
  - "transportar excepciones entre subprocesos"
  - "copy_exception"
  - "rethrow_exception"
  - "mover excepciones entre subprocesos"
ms.assetid: 5c95d57b-acf5-491f-8122-57c5df0edd98
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Transportar excepciones entre subprocesos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C++ admite *transportar una excepción* desde un subproceso a otro. El transporte de excepciones permite detectar una excepción en un subproceso y hacer que parezca que la excepción se produce en un subproceso diferente. Por ejemplo, esta característica se puede utilizar para escribir una aplicación multiproceso en la que el subproceso principal controla todas las excepciones producidas por sus subprocesos secundarios. El transporte de excepciones es útil principalmente para los desarrolladores que crean bibliotecas de programación o sistemas paralelos. Para implementar el transporte de excepciones, Visual C++ proporciona el [exception_ptr](../Topic/exception_ptr.md) tipo y la [current_exception](../Topic/current_exception.md), [rethrow_exception](../Topic/rethrow_exception.md), y [make_exception_ptr](../Topic/make_exception_ptr.md) funciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace std   
{  
   typedef unspecified exception_ptr;   
   exception_ptr current_exception();  
   void rethrow_exception(exception_ptr p);  
   template<class E>   
       exception_ptr make_exception_ptr(E e) noexcept;  
}  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`unspecified`|Clase interna sin especificar que se utiliza para implementar el tipo `exception_ptr`.|  
|`p`|Objeto `exception_ptr` que hace referencia a una excepción.|  
|`E`|Clase que representa una excepción.|  
|`e`|Instancia de la clase del parámetro `E`.|  
  
## <a name="return-value"></a>Valor devuelto  
 La función `current_exception` devuelve un objeto `exception_ptr` que hace referencia a la excepción que está en curso actualmente. Si no hay ninguna excepción en curso, la función devuelve un objeto `exception_ptr` que no está asociado a ninguna excepción.  
  
 La función `make_exception_ptr` devuelve un objeto `exception_ptr` que hace referencia a la excepción especificada por el parámetro `e`.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="scenario"></a>Escenario  
 Suponga que desea crear una aplicación que se pueda escalar para controlar una cantidad de trabajo variable. Para lograr este objetivo, diseña una aplicación multiproceso en la que un subproceso principal inicial crea tantos subprocesos secundarios como necesita para hacer el trabajo. Los subprocesos secundarios ayudan al subproceso principal a administrar los recursos, equilibrar las cargas y mejorar el rendimiento. Al distribuir el trabajo, la aplicación multiproceso funciona mejor que una aplicación uniproceso.  
  
 Sin embargo, si un subproceso secundario produce una excepción, subproceso principal debe controlarla. Esto es porque desea que la aplicación controle las excepciones de una manera coherente y unificada independientemente del número de subprocesos secundarios.  
  
## <a name="solution"></a>Soluciones  
 Para controlar el escenario anterior, el estándar de C++ admite transportar una excepción entre subprocesos. Si un subproceso secundario produce una excepción, esa excepción se convierte en el *excepción actual*. Por analogía con el mundo real, la excepción actual se dice que *en vuelo*. La excepción actual está en vuelo desde el momento en que se produce hasta que el controlador de excepciones que la captura vuelve.  
  
 El subproceso secundario puede detectar la excepción actual en un bloque `catch` y llamar después a la función `current_exception` para almacenar la excepción en un objeto `exception_ptr`. El objeto `exception_ptr` debe estar disponible para el subproceso secundario y para el subproceso principal. Por ejemplo, el objeto `exception_ptr` puede ser una variable global cuyo acceso esté controlado mediante una exclusión mutua. El término *transportar una excepción* significa una excepción en un subproceso se puede convertir a un formulario que puede obtenerse mediante otro subproceso.  
  
 A continuación, el subproceso principal llama a la función `rethrow_exception`, que extrae y produce la excepción desde el objeto `exception_ptr`. Cuando se produce la excepción, se convierte en la excepción actual del subproceso principal. Es decir, parece que la excepción procede del subproceso principal.  
  
 Por último, el subproceso principal puede detectar la excepción actual en un bloque `catch` y después procesarla o producirla en un controlador de excepciones de nivel superior. O bien, el subproceso principal puede omitir la excepción y permitir que el proceso finalice.  
  
 La mayoría de las aplicaciones no tienen que transportar excepciones entre subprocesos. Sin embargo, esta característica es útil en un sistema informático en paralelo porque el sistema puede repartir el trabajo entre los subprocesos secundarios, los procesadores o los núcleos. En un entorno informático en paralelo, un único subproceso dedicado puede controlar todas las excepciones de los subprocesos secundarios y puede presentar un modelo coherente de control de excepciones a cualquier aplicación.  
  
 Para obtener más información sobre la propuesta del comité de normas de C++, busque en Internet el número de documento N2179, titulado "Language Support for Transporting Exceptions between Threads" (Compatibilidad con lenguajes para transportar excepciones entre subprocesos).  
  
## <a name="exception-handling-models-and-compiler-options"></a>Modelos de control de excepciones y opciones del compilador  
 El modelo de control de excepciones de una aplicación determina si puede detectar y transportar una excepción. Visual C++ admite tres modelos que pueden controlar excepciones de C++, excepciones de Control de excepciones estructurado (SEH) y excepciones de Common Language Runtime (CLR). Utilice la [/EH](../build/reference/eh-exception-handling-model.md) y [/CLR](../build/reference/clr-common-language-runtime-compilation.md) Opciones del compilador para especificar el modelo de control de excepciones de la aplicación.  
  
 Solo la combinación siguiente de opciones del compilador e instrucciones de programación puede transportar una excepción. Otras combinaciones no pueden detectar excepciones, o pueden detectar pero no pueden transportar excepciones.  
  
-   El **/EHa** opción del compilador y el `catch` instrucción puede transportar excepciones de SEH y C++.  
  
-   El **/EHa**, **/EHs**, y **/EHsc** Opciones del compilador y el `catch` instrucción puede transportar excepciones de C++.  
  
-   El **/CLR** o **/clr: pure** opción del compilador y el `catch` instrucción puede transportar excepciones de C++. El **/CLR** Opciones del compilador implican la especificación de la **/EHa** opción. Tenga en cuenta que el compilador no admite transportar excepciones administradas. Esto es porque las excepciones administradas, que se derivan de la [clase System.Exception](../standard-library/exception-class1.md), ya son objetos que se pueden mover entre subprocesos mediante las funciones de common language runtime.  
  
    > [!IMPORTANT]
    >  Se recomienda que especifique el **/EHsc** opción del compilador y detecte solo las excepciones de C++. Se expone a una amenaza de seguridad si utiliza la **/EHa** o **/CLR** opción del compilador y un **catch** instrucción con puntos suspensivos *declaración de excepción* (`catch(...)`). Probablemente piense utilizar la instrucción `catch` para capturar algunas excepciones concretas. Sin embargo, la instrucción `catch(...)` captura todas las excepciones de C++ y SEH, incluidas las inesperadas que deben ser irrecuperables. Si se omite o se controla mal una excepción inesperada, el código malintencionado puede aprovechar esa oportunidad para socavar la seguridad del programa.  
  
## <a name="usage"></a>Uso  
 Las secciones siguientes describen cómo transportar excepciones mediante la `exception_ptr` tipo y el `current_exception`, `rethrow_exception`, y `make_exception_ptr` funciones.  
  
### <a name="exceptionptr-type"></a>Tipo exception_ptr  
 Utilice un objeto `exception_ptr` para hacer referencia a la excepción actual o a una instancia de una excepción especificada por el usuario. En la implementación de Microsoft, una excepción se representa mediante un [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) estructura. Cada objeto `exception_ptr` incluye un campo de referencia de excepción que apunta a una copia de la estructura `EXCEPTION_RECORD` que representa la excepción.  
  
 Cuando se declara una variable `exception_ptr`, la variable no está asociada a ninguna excepción. Es decir, su campo de referencia de excepción es NULL. Tales un `exception_ptr` objeto se denomina un *exception_ptr null*.  
  
 Utilice la función `current_exception` o `make_exception_ptr` para asignar una excepción a un objeto `exception_ptr`. Cuando se asigna una excepción a una variable `exception_ptr`, el campo de referencia de excepción de la variable apunta a una copia de la excepción. Si no hay memoria suficiente para copiar la excepción, el campo de referencia de excepción apunta a una copia de un [std:: bad_alloc](../standard-library/bad-alloc-class.md) excepción. Si el `current_exception` o `make_exception_ptr` función no puede copiar la excepción por cualquier otro motivo, las llamadas de función el [Finalizar](../c-runtime-library/reference/terminate-crt.md) función para salir del proceso actual.  
  
 A pesar de su nombre, un objeto `exception_ptr` no es en sí mismo un puntero. No obedece a la semántica de los punteros y no se puede utilizar con los operadores de acceso (`->`) o de direccionamiento indirecto (*) de miembro de puntero. El objeto `exception_ptr` no tiene ningún miembro de datos ni ninguna función miembro de tipo público.  
  
 **Comparaciones:**  
  
 Se pueden usar los operadores de igualdad (`==`) y desigualdad (`!=`) para comparar dos objetos `exception_ptr`. Los operadores no comparan el valor binario (patrón de bits) de las estructuras `EXCEPTION_RECORD` que representan las excepciones. En su lugar, los operadores comparan las indicaciones del campo de referencia de excepción de los objetos `exception_ptr`. Por tanto, un `exception_ptr` NULL y el valor NULL se consideran iguales.  
  
### <a name="currentexception-function"></a>Función current_exception  
 Llame a la función `current_exception` en un bloque `catch`. Si una excepción está en vuelo y el bloque `catch` puede detectarla, la función `current_exception` devuelve un objeto `exception_ptr` que hace referencia a la excepción. De lo contrario, la función devuelve un objeto `exception_ptr` NULL.  
  
 **Detalles:**  
  
 El `current_exception` función captura la excepción que está en vuelo independientemente de si el `catch` instrucción especifica un [declaración de excepción](../cpp/try-throw-and-catch-statements-cpp.md) instrucción.  
  
 Se llama al destructor de la excepción actual al final del bloque `catch` si no vuelve a producir la excepción. Sin embargo, incluso cuando se invoca el `current_exception` función de destructor, la función devuelve un `exception_ptr` objeto que hace referencia a la excepción actual.  
  
 Las llamadas sucesivas a la función `current_exception` devuelven objetos `exception_ptr` que hacen referencia a distintas copias de la excepción actual. Por tanto, al comparar los objetos se consideran diferentes porque hacen referencia a copias distintas, incluso aunque las copias tengan el mismo valor binario.  
  
 **Excepciones SEH:**  
  
 Si utiliza el **/EHa** opción del compilador, que puede detectar una excepción SEH en C++ `catch` bloque. La función `current_exception` devuelve un objeto `exception_ptr` que hace referencia a la excepción SEH. Y el `rethrow_exception` función produce la excepción SEH si se le llama con thetransported `exception_ptr` objeto como su argumento.  
  
 La función `current_exception` devuelve un `exception_ptr` NULL si se le llama en un controlador de terminación de SEH `__finally`, un controlador de excepciones `__except` o la expresión de filtro `__except`.  
  
 Una excepción transportada no admite excepciones anidadas. Se genera una excepción anidada si se produce otra excepción mientras se está controlando una excepción. Si se detecta una excepción anidada, el miembro de datos `EXCEPTION_RECORD.ExceptionRecord` apunta a una cadena de estructuras `EXCEPTION_RECORD` que describen las excepciones asociadas. La función `current_exception` no admite excepciones anidadas porque devuelve un objeto `exception_ptr` cuyo miembro de datos `ExceptionRecord` se pone a cero.  
  
 Si se detecta una excepción SEH, debe administrar la memoria a la que hace referencia cualquier puntero en la matriz de miembros de datos `EXCEPTION_RECORD.ExceptionInformation`. Debe garantizar que la memoria es válida mientras dura el objeto `exception_ptr` correspondiente y que la memoria se liberará cuando se elimine el objeto `exception_ptr`.  
  
 Puede utilizar funciones de traductor de excepciones estructuradas (SE) junto con la característica de transporte de excepciones. Si una excepción SEH se traduce a una excepción de C++, la función `current_exception` devuelve un `exception_ptr` que hace referencia a la excepción traducida en lugar de a la excepción SEH original. La función `rethrow_exception` produce posteriormente la excepción traducida, no la excepción original. Para obtener más información acerca de las funciones de traductor de SE, consulte [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).  
  
### <a name="rethrowexception-function"></a>Función rethrow_exception  
 Después de almacenar una excepción detectada en un objeto `exception_ptr`, el subproceso principal puede procesar el objeto. En el subproceso principal, llame a la función `rethrow_exception` junto con el objeto `exception_ptr` como argumento. La función `rethrow_exception` extrae la excepción del objeto `exception_ptr` y después produce la excepción en el contexto del subproceso principal. Si el `p` parámetro de la `rethrow_exception` función es un valor null `exception_ptr`, la función produce [std:: bad_exception](../standard-library/bad-exception-class.md).  
  
 La excepción extraída es ahora la excepción actual en el subproceso principal y puede controlarla como haría con cualquier otra excepción. Si se detecta la excepción, puede controlarla inmediatamente o utilizar una instrucción `throw` para enviarla a un controlador de excepciones de nivel superior. De lo contrario, no haga nada y deje que el controlador de excepciones predeterminado del sistema finalice el proceso.  
  
### <a name="makeexceptionptr-function"></a>Función make_exception_ptr  
 La función `make_exception_ptr` toma una instancia de una clase como argumento y devuelve un `exception_ptr` que hace referencia a la instancia. Normalmente, se especifica un [clase exception](../standard-library/exception-class1.md) objeto como argumento para el `make_exception_ptr` funcione, aunque el argumento puede ser cualquier objeto de clase.  
  
 Llamar a la función `make_exception_ptr` equivale a producir una excepción de C++, detectarla en un bloque `catch` y llamar después a la función `current_exception` para devolver un objeto `exception_ptr` que hace referencia a la excepción. La implementación de Microsoft de la función `make_exception_ptr` es más eficaz que producir y detectar después una excepción.  
  
 Una aplicación no suele necesitar la función `make_exception_ptr` y desaconsejamos su uso.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se transporta una excepción estándar de C++ y una excepción personalizada de C++ de un subproceso a otro.  
  
```  
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
 **Encabezado:** \< (excepción)>  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)   
 [Estructura EXCEPTION_RECORD](#base.exception_record_str)   
 [Sintaxis del controlador](#base.handler_syntax)   
 [/EH (modelo de control de excepciones)](../build/reference/eh-exception-handling-model.md)   
 [/CLR (compilación de common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)