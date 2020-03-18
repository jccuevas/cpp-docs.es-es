---
title: '&lt;exception&gt; (Funciones)'
ms.date: 11/04/2016
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
helpviewer_keywords:
- std::current_exception [C++]
- std::get_terminate [C++]
- std::get_unexpected [C++]
- std::make_exception_ptr [C++]
- std::rethrow_exception [C++]
- std::set_terminate [C++]
- std::set_unexpected [C++]
- std::terminate [C++]
- std::uncaught_exception [C++]
- std::unexpected [C++]
ms.openlocfilehash: 34a34c48be8bb0e319a7d0eebeccba805cafbc1f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424828"
---
# <a name="ltexceptiongt-functions"></a>&lt;exception&gt; (Funciones)

## <a name="current_exception"></a>current_exception

Obtiene un puntero inteligente a la excepción actual.

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>Valor devuelto

Objeto [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) que apunta a la excepción actual.

### <a name="remarks"></a>Observaciones

Llame a la función `current_exception` en un bloque catch. Si una excepción está en vuelo y el bloque catch puede detectarla, la función `current_exception` devuelve un objeto `exception_ptr` que hace referencia a la excepción. De lo contrario, la función devuelve un objeto `exception_ptr` NULL.

La función `current_exception` captura la excepción que está en vuelo independientemente de si la instrucción **catch** especifica una instrucción [de declaración de excepción](../cpp/try-throw-and-catch-statements-cpp.md) .

Se llama al destructor de la excepción actual al final del bloque **catch** si no se vuelve a producir la excepción. En cambio, incluso aunque llame a la función`current_exception` en el destructor, la función devuelve un objeto `exception_ptr` que hace referencia a la excepción actual.

Las llamadas sucesivas a la función `current_exception` devuelven objetos `exception_ptr` que hacen referencia a distintas copias de la excepción actual. Por tanto, al comparar los objetos se consideran diferentes porque hacen referencia a copias distintas, incluso aunque las copias tengan el mismo valor binario.

## <a name="make_exception_ptr"></a>make_exception_ptr

Crea un objeto [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) que contiene una copia de una excepción.

```cpp
template <class E>
    exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>Parámetros

*Excepto*\
Clase con la excepción que se va a copiar. Normalmente, se especifica un objeto [exception (Clase)](../standard-library/exception-class.md) como argumento para la función `make_exception_ptr`, aunque el argumento puede ser cualquier objeto de clase.

### <a name="return-value"></a>Valor devuelto

Objeto [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) que apunta a una copia de la excepción actual para *Except*.

### <a name="remarks"></a>Observaciones

Llamar a la función `make_exception_ptr` equivale a iniciar una excepción de C++, detectarla en un bloque catch y llamar después a la función [current_exception](../standard-library/exception-functions.md#current_exception) para devolver un objeto `exception_ptr` que hace referencia a la excepción. La implementación de Microsoft de la función `make_exception_ptr` es más eficaz que producir y detectar después una excepción.

Una aplicación no suele necesitar la función `make_exception_ptr` y desaconsejamos su uso.

## <a name="rethrow_exception"></a>rethrow_exception

Inicia una excepción pasada como parámetro.

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>Parámetros

*P*\
Excepción detectada que se va a volver a iniciar. Si *P* es un [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)nulo, la función produce [STD:: bad_exception](../standard-library/bad-exception-class.md).

### <a name="remarks"></a>Observaciones

Después de almacenar una excepción detectada en un objeto `exception_ptr`, el subproceso principal puede procesar el objeto. En el subproceso principal, llame a la función `rethrow_exception` junto con el objeto `exception_ptr` como argumento. La función `rethrow_exception` extrae la excepción del objeto `exception_ptr` y después produce la excepción en el contexto del subproceso principal.

## <a name="get_terminate"></a>get_terminate

Obtiene la función `terminate_handler` actual.

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a>set_terminate

Establece un nuevo `terminate_handler` al que se llamará cuando finalice el programa.

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>Parámetros

\ *fnew*
Función a la que se va a llamar en la finalización.

### <a name="return-value"></a>Valor devuelto

Dirección de la función anterior al a que se solía llamar en la finalización.

### <a name="remarks"></a>Observaciones

La función establece un nuevo [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) como la función * *fnew*. Por lo tanto, *fnew* no debe ser un puntero nulo. La función devuelve la dirección del controlador de finalización anterior.

### <a name="example"></a>Ejemplo

```cpp
// exception_set_terminate.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void termfunction()
{
    cout << "My terminate function called." << endl;
    abort();
}

int main()
{
    terminate_handler oldHandler = set_terminate(termfunction);

    // Throwing an unhandled exception would also terminate the program
    // or we could explicitly call terminate();

    //throw bad_alloc();
    terminate();
}
```

## <a name="get_unexpected"></a>get_unexpected

Obtiene la función `unexpected_handler` actual.

```cpp
unexpected_handler get_unexpected();
```

## <a name="rethrow_if_nested"></a>rethrow_if_nested

```cpp
template <class E> 
    void rethrow_if_nested(const E& e);
```

### <a name="remarks"></a>Observaciones

Si no es un tipo de clase polimórfica, o si `nested_exception` es inaccesible o ambiguo, no hay ningún efecto. De lo contrario, realiza una conversión dinámica.

## <a name="set_unexpected"></a>set_unexpected

Establece un nuevo `unexpected_handler` cuando se encuentra una excepción inesperada.

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>Parámetros

\ *fnew*
Función a la que se llamará cuando se encuentre una excepción inesperada.

### <a name="return-value"></a>Valor devuelto

Dirección del `unexpected_handler` anterior.

### <a name="remarks"></a>Observaciones

*fnew* no debe ser un puntero nulo.

El estándar de C++ requiere que se llame a `unexpected` cuando una función inicie una excepción que no está en su lista de excepciones. La implementación actual no lo admite. En el ejemplo siguiente se llama a `unexpected` directamente, que llama a `unexpected_handler`.

### <a name="example"></a>Ejemplo

```cpp
// exception_set_unexpected.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void uefunction()
{
    cout << "My unhandled exception function called." << endl;
    terminate(); // this is what unexpected() calls by default
}

int main()
{
    unexpected_handler oldHandler = set_unexpected(uefunction);

    unexpected(); // library function to force calling the
                  // current unexpected handler
}
```

## <a name="terminate"></a>cancela

Llama a un controlador de finalización.

```cpp
void terminate();
```

### <a name="remarks"></a>Observaciones

La función llama a un controlador de finalización, una función de tipo **void**. Si el programa llama directamente a `terminate`, el controlador de finalización es el último que se establece mediante una llamada a [set_terminate](../standard-library/exception-functions.md#set_terminate). Si se llama a `terminate` por algún otro motivo durante la evaluación de una expresión Throw, el controlador de finalización es el que está en vigor inmediatamente después de evaluar la expresión Throw.

Un controlador de finalización no puede volver a su llamador. Al iniciar el programa, el controlador de finalización es una función que llama a `abort`.

### <a name="example"></a>Ejemplo

Vea [set_unexpected](../standard-library/exception-functions.md#set_unexpected) para obtener un ejemplo de uso de `terminate`.

## <a name="throw_with_nested"></a>throw_with_nested

```cpp
template <class T> [[noreturn]]
    void throw_with_nested(T&& t);
```

### <a name="remarks"></a>Observaciones

Produce una excepción con excepciones anidadas.

## <a name="uncaught_exception"></a>uncaught_exception

Devuelve **True** solo si se está procesando actualmente una excepción iniciada.

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>Valor devuelto

Devuelve **true** después de completar la evaluación de una expresión Throw y antes de completar la inicialización de la declaración de excepción en el controlador coincidente o llamando a [inesperada](../standard-library/exception-functions.md#unexpected) como resultado de la expresión Throw. En concreto, `uncaught_exception` devolverá **true** cuando se llama desde un destructor que se invoca durante un desenredo de excepciones. En dispositivos, `uncaught_exception` solo se admite en Windows CE 5.00 y versiones posteriores, incluidas las plataformas Windows Mobile 2005.

### <a name="example"></a>Ejemplo

```cpp
// exception_uncaught_exception.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>
#include <string>

class Test
{
public:
   Test( std::string msg ) : m_msg( msg )
   {
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;
   }
   ~Test( )
   {
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl
         << "        std::uncaught_exception( ) = "
         << std::uncaught_exception( )
         << std::endl;
   }
private:
    std::string m_msg;
};

// uncaught_exception will be true in the destructor
// for the object created inside the try block because
// the destructor is being called as part of the unwind.

int main( void )
   {
      Test t1( "outside try block" );
      try
      {
         Test t2( "inside try block" );
         throw 1;
      }
      catch (...) {
   }
}
```

```Output
In Test::Test("outside try block")
In Test::Test("inside try block")
In Test::~Test("inside try block")
        std::uncaught_exception( ) = 1
In Test::~Test("outside try block")
        std::uncaught_exception( ) = 0
```

## <a name="unexpected"></a>esperado

Llama al controlador inesperado.

```cpp
void unexpected();
```

### <a name="remarks"></a>Observaciones

El estándar de C++ requiere que se llame a `unexpected` cuando una función inicie una excepción que no está en su lista de excepciones. La implementación actual no lo admite. El ejemplo llama a `unexpected` directamente, que llama al controlador inesperado.

La función llama a un controlador inesperado, una función de tipo **void**. Si el programa llama directamente a `unexpected`, el controlador inesperado es el establecido más recientemente por una llamada a [set_unexpected](../standard-library/exception-functions.md#set_unexpected).

Un controlador inesperado no puede volver a su llamador. Puede finalizar la ejecución al:

- Iniciar un objeto de un tipo enumerado en la especificación de excepción o un objeto de cualquier tipo, si el programa llama directamente al controlador inesperado.

- Iniciar un objeto de tipo [bad_exception](../standard-library/bad-exception-class.md).

- Llamar a [Terminate](../standard-library/exception-functions.md#terminate), `abort` o **Exit**(`int`).

Al inicio del programa, el controlador inesperado es una función que llama a [terminate](../standard-library/exception-functions.md#terminate).

### <a name="example"></a>Ejemplo

Vea [set_unexpected](../standard-library/exception-functions.md#set_unexpected) para obtener un ejemplo de uso de `unexpected`.
