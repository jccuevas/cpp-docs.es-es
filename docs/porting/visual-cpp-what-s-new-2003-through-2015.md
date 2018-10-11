---
title: Novedades de Visual C++ de 2003 a 2015 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 01ee370b4fd96419ce095fa9a93450b98b241dd2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448576"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Novedades de Visual C++ de 2003 a 2015

En esta página, se recopilan todas las páginas de novedades de todas las versiones de Visual C++, de Visual Studio 2015 a 2003. Esta información se pone a su disposición en caso de que pueda servir de ayuda al actualizar desde versiones anteriores de Visual C++.

> [!NOTE]
> Para obtener más información sobre Visual Studio 2017, consulte [What's new for Visual C++ in Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) (Novedades de Visual C++ en Visual Studio 2017) y [Conformance Improvements in Visual C++ in Visual Studio 2017](../cpp-conformance-improvements-2017.md) (Mejoras de conformidad de Visual C++ en Visual Studio 2017).

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Novedades de C++ en Visual Studio 2015

En Visual Studio 2015 y versiones posteriores, las mejoras continuas en la conformidad del compilador a veces pueden cambiar la manera en que este entiende el código fuente existente. Cuando esto sucede, pueden producirse errores nuevos o diferentes durante la compilación o puede haber incluso diferencias de comportamiento en el código previamente compilado que parecía ejecutarse correctamente.

Afortunadamente, estas diferencias tienen poco o ningún efecto en la mayoría del código fuente y cuando se necesitan código fuente u otros cambios para resolver estas diferencias, las correcciones suelen ser pequeñas y sencillas. Hemos incluido muchos ejemplos de código fuente previamente aceptable que es posible que deba cambiarse *(antes)* y las revisiones para corregirlos *(después)*.

Aunque estas diferencias pueden afectar a su código fuente u otros artefactos de compilación, no afectan a la compatibilidad binaria entre actualizaciones de versiones de Visual C++. Un tipo de cambio más drástico, el *cambio importante*, puede afectar a la compatibilidad binaria, pero este tipo de alteraciones de compatibilidad binaria solo se producen entre las versiones principales de Visual C++. por ejemplo, entre Visual C++ 2013 y Visual C++ 2015. Para obtener información sobre los cambios importantes que se produjeron entre Visual C++ 2013 y Visual C++ 2015, vea [Historial de cambios en Visual C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md).

- [Mejoras de conformidad en Visual Studio 2015](#VS_RTM)

- [Mejoras de conformidad en Visual Studio 2015 Update 1](#VS_Update1)

- [Mejoras de conformidad en Visual Studio 2015 Update 2](#VS_Update2)

- [Mejoras de conformidad en Visual Studio 2015 Update 3](#VS_Update3)

### <a name="VS_RTM"></a> Mejoras de conformidad en Visual Studio 2015

- **/Zc:forScope- (opción)**

   La opción del compilador `/Zc:forScope-` está en desuso y se quitará en una próxima versión.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Esta opción solía usarse para que el código no estándar que usa las variables de bucle se pudiese usar después del punto donde, según el estándar, debería quedar fuera del ámbito. Solo era necesario al compilar con la opción `/Za`, ya que sin `/Za`, siempre se permite usar una variable de bucle for tras el final del bucle. Si no le interesa el cumplimiento de los estándares (por ejemplo, si su código no está destinado a otros compiladores), puede desactivar la opción `/Za` (o establecer la propiedad **Deshabilitar extensiones de lenguaje** en **No**). Si le interesa escribir código portable y compatible con los estándares, debe volver a escribir el código de modo que se ajuste a la norma. Para ello, mueva la declaración de dichas variables a un punto fuera del bucle.

   ```cpp
    // zc_forScope.cpp
    // compile with: /Zc:forScope- /Za
    // C2065 expected
    int main() {
       // Uncomment the following line to resolve.
       // int i;
       for (int i =0; i < 1; i++)
          ;
       i = 20;   // i has already gone out of scope under /Za
    }
   ```

- **Opción del compilador /Zg.**

   La opción de compilador `/Zg` (Generar prototipos de función) ya no está disponible. Esta opción del compilador quedó en desuso anteriormente.

- Ya no se pueden ejecutar pruebas unitarias con C++/CLI desde la línea de comandos con mstest.exe. En su lugar, use vstest.console.exe.

- **Palabra clave mutable.**

   El especificador de clase de almacenamiento **mutable** ya no se permite en lugares donde anteriormente se compilaba sin errores. Ahora, el compilador produce el error C2071 (clase de almacenamiento no válida). Según el estándar, el especificador mutable solo puede aplicarse a los nombres de miembros de datos de clase; no puede aplicarse a los nombres declarados como const o static y tampoco para hacer referencia a los miembros.

   Por ejemplo, considere el siguiente código:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Las versiones anteriores del compilador de Visual C++ aceptaban esto, pero ahora el compilador produce el siguiente error:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Para corregir el error, basta con quitar la palabra clave **mutable** redundante.

- **char_16_t y char32_t**

   Ya no puede usar `char16_t` o `char32_t` como alias en una definición de tipo (typedef), ya que estos tipos ahora se consideran integrados. Era habitual que los usuarios y creadores de bibliotecas definieran `char16_t` y `char32_t` como alias de `uint16_t` y `uint32_t`, respectivamente.

   ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
    uint16_t x = 1; uint32_t y = 2;
    char16_t a = x;
    char32_t b = y;
    return 0;
    }
   ```

   Para actualizar el código, quite las declaraciones **typedef** y cambie el nombre de todos los identificadores que estén en conflicto con estos nombres.

- **Parámetros de plantilla sin tipo**

   Hay determinado código que implica parámetros de plantilla sin tipo en el que ahora se comprueba la compatibilidad de tipos cuando se proporcionan argumentos de plantilla explícitos. Por ejemplo, el código siguiente se compilaba sin errores en las versiones anteriores de Visual C++.

   ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}        
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
   ```

   El compilador actual produce correctamente un error, porque el tipo de parámetro de plantilla no coincide con el argumento de plantilla (el parámetro es un puntero a miembro const, pero la función f no es const):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Para solucionar este error en el código, asegúrese de que el tipo del argumento de la plantilla que está usando coincide con el tipo declarado del parámetro de plantilla.

- **__declspec(align)**

   El compilador ya no acepta `__declspec(align)` en las funciones. Esto siempre se ignoraba, pero ahora produce un error del compilador.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Para solucionar este problema, quite `__declspec(align)` de la declaración de función. Puesto que no tenía ningún efecto, el hecho de quitarlo no cambia nada.

- **Control de excepciones**

   Hay un par de cambios en el control de excepciones. En primer lugar, los objetos de excepción deben poderse copiar o mover. El siguiente código se compila en Visual Studio 2013, pero no en Visual Studio 2015:

   ```cpp
    struct S {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   El problema es que el constructor de copias es privado, por lo que el objeto no se puede copiar como cuando se controla una excepción de la manera habitual. Lo mismo sucede cuando el constructor de copias se declara **explicit**.

   ```cpp
    struct S {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   Para actualizar el código, asegúrese de que el constructor de copias correspondiente al objeto de excepción es público y no esté marcado como **explicit**.

   Para detectar una excepción por valor, también es necesario que el objeto de excepción se pueda copiar. El siguiente código se compila en Visual Studio 2013, pero no en Visual Studio 2015:

   ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
   ```

   Para solucionar este problema, cambie el tipo de parámetro de **catch** a una referencia.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Literales de cadena seguidos de macros**

   El compilador ahora admite literales definidos por el usuario. En consecuencia, los literales de cadena seguidos de macros sin ningún espacio en blanco intermedio se interpretan como literales definidos por el usuario, lo que puede dar lugar a errores o resultados inesperados. Por ejemplo, en los compiladores anteriores el código siguiente se compilaba perfectamente:

   ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
   ```

   El compilador interpretaba esto como un literal de cadena “hello” seguido de una macro, expandida en “there” y, a continuación, los dos literales de cadena se concatenaban en uno solo. En Visual Studio 2015, el compilador interpreta esto como un literal definido por el usuario, pero dado que no hay ningún literal coincidente _x definido por el usuario, produce un error.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Para solucionar este problema, agregue un espacio entre el literal de cadena y la macro.

- **Literales de cadena adyacentes**

   Como en el caso anterior, en versiones anteriores de Visual C++ y debido a los cambios relacionados con el análisis de cadenas, los literales de cadena adyacentes (ya fueran literales de cadena de caracteres anchos o estrechos) sin ningún espacio en blanco se interpretaban como una sola cadena concatenada. En Visual Studio 2015, ahora debe agregarse un espacio en blanco entre las dos cadenas. Por ejemplo, el código siguiente debe modificarse:

   ```cpp
    char * str = "abc""def";
   ```

   Simplemente agregue un espacio entre las dos cadenas.

   ```cpp
    char * str = "abc" "def";
   ```

- **Placement new y delete**

   Se ha realizado un cambio en el operador **delete** a fin de adaptarlo al estándar de C++14. Detalles del cambio de los estándares se pueden encontrar en la página de [desasignación de ajuste de tamaño de C++](http://isocpp.org/files/papers/n3778.html). Los cambios agregan un formulario del operador **delete** global que toma un parámetro de tamaño. La novedad es que si antes usaba un operador **delete** con la misma firma (para que se correspondiese con un operador **placement new**), ahora recibirá un error del compilador (C2956, que se produce en el punto donde se usa **placement new**, ya que es la posición en el código en la que el compilador intenta identificar un operador **delete** coincidente adecuado).

   La función `void operator delete(void *, size_t)` era un operador **placement delete** correspondiente a la función **placement new**  `void * operator new(size_t, size_t)` en C++11. Con la desasignación con tamaño de C ++ 14, esta función **delete** es ahora una *función de desasignación habitual* (operador **delete** global). Según el estándar, si el uso de **placement new** busca una función **delete** correspondiente y encuentra una función de desasignación habitual, el programa tendrá un formato incorrecto.

   Supongamos, por ejemplo, que el código define tanto **placement new** como **placement delete**:

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   El problema se produce debido a la coincidencia de las firmas de función entre un operador **placement delete** definido y el nuevo operador global **delete** con tamaño. Analice si puede usar un tipo que no sea `size_t` para los operadores **placement new** y **delete**.  Tenga en cuenta que **typedef** de `size_t` depende del compilador; es un **typedef** para **int sin signo** en Visual C++. Una buena solución es que use un tipo enumerado como el siguiente:

   ```cpp
    enum class my_type : size_t {};
   ```

   A continuación, cambie la definición de **placement new** y **delete** para usar este tipo como el segundo argumento en lugar de `size_t`. También es necesario que actualice las llamadas a **placement new** para pasar el nuevo tipo (por ejemplo, con `static_cast<my_type>` para convertir a partir del valor entero) y que actualice la definición de **new** y **delete** para realizar la conversión al tipo entero. No es necesario usar **enum** para esto; un tipo de clase con un miembro `size_t` también funcionaría.

   Una solución alternativa es que pueda eliminar por completo **placement new**. Si el código usa **placement new** para implementar un bloque de memoria donde el argumento placement sea el tamaño del objeto que se va a asignar o eliminar, entonces podría usarse la característica de desasignación con tamaño para reemplazar su propio código de bloque de memoria personalizado, y así deshacerse de las funciones placement y usar simplemente su propio operador **delete** de dos argumentos en lugar de las funciones placement.

   Si no quiere actualizar su código de forma inmediata, puede recuperar el comportamiento anterior mediante la opción de compilador `/Zc:sizedDealloc-`. Si usa esta opción, las funciones **delete** de dos argumentos no existen y no se provocará un conflicto con el operador **placement delete**.

- **Miembros de datos de uniones**

   Los miembros de datos de uniones ya no pueden tener tipos de referencia. El siguiente código se compila en Visual Studio 2013, pero genera un error en Visual Studio 2015.

   ```cpp
    union U1 {
        const int i;
    };
    union U2 {
       int &i;
    };
    union U3 {
        struct {int &i;};
    };
   ```

   El código anterior produce los errores siguientes:

   ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
   ```

   Para solucionar este problema, cambie los tipos de referencia a un puntero o a un valor. Para poder cambiar el tipo a un puntero, hay que hacer cambios en el código que usa el campo union. Si se cambia el código a un valor, también cambian los datos almacenados en la unión, lo que afecta a otros campos, ya que los campos de tipos union comparten la misma memoria. En función del tamaño del valor, también podrá cambiar el tamaño de la unión.

- Las **uniones anónimas**

   ahora se ajustan mejor al estándar. Las versiones anteriores del compilador generaban un constructor y destructor explícitos para uniones anónimas. Estos se eliminan en Visual Studio 2015.

   ```cpp
    struct S {
      S();
     };

     union {
      struct {
       S s;
      };
     } u; // C2280
   ```

   El código anterior genera el error siguiente en Visual Studio 2015:

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   Para resolver este problema, proporcione sus propias definiciones del constructor o del destructor.

   ```cpp
    struct S {
    // Provide a default constructor by adding an empty function body.
    S() {}
    };

    union {
    struct {
    S s;
    };
    } u;
   ```

- **Uniones con estructuras anónimas**

   Para cumplir con el estándar, el comportamiento de runtime ha cambiado para los miembros de estructuras anónimas en uniones. El constructor de miembros de estructura anónima de una unión ya no se llama implícitamente cuando se crea este tipo de unión. Además, el destructor de miembros de estructura anónima de una unión ya no se llama implícitamente cuando la unión sale del ámbito. Analice el siguiente código, en el que una unión U contiene una estructura anónima que a su vez contiene a un miembro que es una estructura con nombre S que tiene un destructor.

   ```cpp
    #include <stdio.h>
    struct S {
        S() { printf("Creating S\n"); }
        ~S(){ printf("Destroying S\n"); }
    };
    union U {
        struct {
        S s;
    };
        U() {}
        ~U(){}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   En Visual Studio 2013, se llama al constructor de S cuando se crea la unión, y se llama al destructor de S cuando se limpia la pila de la función f. Pero en Visual Studio 2015, no se llama al constructor ni al destructor. El compilador emite una advertencia sobre este cambio de comportamiento.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Para restaurar el comportamiento original, asigne un nombre a la estructura anónima. El comportamiento en tiempo de ejecución de las estructuras no anónima es el mismo, independientemente de la versión del compilador.

   ```cpp
    #include <stdio.h>

    struct S {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   Por otro lado, intente mover el código del constructor y el destructor a funciones nuevas y agregue llamadas a estas funciones desde el constructor y el destructor de la unión.

   ```cpp
    #include <stdio.h>

    struct S {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        };
        U() { s.Create();  }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

    char s[1024];
    printf("Press any key.\n");
    gets_s(s);
    return 0;
    }
   ```

- **Resolución de plantilla**

   Se han hecho cambios en la resolución de nombres de plantillas. En C++, al pensar en candidatos para la resolución de un nombre, puede darse el caso de que uno o más de los nombres considerados como coincidencias posibles produzcan una creación de instancias de plantilla no válida. Normalmente, estas instancias no válidas no provocan errores del compilador; este principio se conoce como SFINAE (Substitution Failure Is Not An Error).

   Ahora, si SFINAE requiere que el compilador cree una instancia de la especialización de una plantilla de clase, los errores que se producen durante este proceso son errores del compilador. En versiones anteriores, el compilador omitiría esos errores. Por ejemplo, considere el siguiente código:

   ```cpp
    #include <type_traits>

    template<typename T>
    struct S
    {
    S() = default;
    S(const S&);
    S(S&&);

    template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type>
    S(S<U>&&);
    };

    struct D;

    void f1()
    {
    S<D> s1;
        S<D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
    S<D> s1;
        S<D> s2(s1);
    }
   ```

   Si usa el compilador actual, obtendrá el siguiente error:

   ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
            with
            [
                T=D,
                U=D
            ]
   ```

   Esto se debe a que el punto de la primera invocación de is_base_of de la clase 'D' aún no se ha definido.

   En este caso, la solución es no usar los rasgos de tipos (type traits) mientras no se defina la clase. Si mueve las definiciones de B y D al principio del archivo de código, el error se soluciona. Si las definiciones están en archivos de encabezado, compruebe el orden de las instrucciones include para los archivos de encabezado a fin de asegurarse de que las definiciones de clase se compilan antes de que se usen las plantillas problemáticas.

- **Constructores de copias**

   Tanto en Visual Studio 2013 como en Visual Studio 2015, el compilador genera un constructor de copias para una clase si esa clase tiene un constructor de movimiento definido por el usuario, pero ningún constructor de copias definido por el usuario. En Dev14, este constructor de copias generado implícitamente también se marca como "= delete".

### <a name="VS_Update1"></a> Mejoras de conformidad en Visual Studio 2015 Update 1

- **Clases base virtuales privadas y herencia indirecta**

   Las versiones anteriores del compilador permiten una clase derivada para llamar a funciones de miembro de sus clases base *derivadas indirectamente*`private virtual` . Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2280 como resultado.

   ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
   ```

   Ejemplo (antes)

   ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle: private virtual base {};class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
   ```

   Ejemplo (después)

   ```cpp
    class base;  // as above

    class middle: protected virtual base {};
    class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

  O bien

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Operador new y operador delete sobrecargados**

   Las versiones anteriores del compilador permitieron que **operator new** no miembro y **operator delete** no miembro se declarasen como static y que se declararan en espacios de nombres distintos del espacio de nombres global.  Este comportamiento anterior provocó el riesgo de que el programa no llamaba a la implementación del operador **new** o **delete** tal y como estaba diseñada por el programador, lo que daba lugar a un comportamiento en tiempo de ejecución incorrecto silencioso. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2323 en su lugar.

   ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
   ```

   Ejemplo (antes)

   ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
   ```

   Ejemplo (después)

   ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
   ```

      Additionally, although the compiler doesn't give a specific diagnostic, inline operator new is considered ill-formed.

- **Llamada a "operator *type*()" (conversión definida por el usuario) en tipos que no sean de clase** Las versiones anteriores del compilador permitieron que se llamara a "operator *type*()" en tipos que no son de clase mientras que se les ignora en modo silencioso. Este comportamiento anterior creó un riesgo de generación de código incorrecto silencioso, lo que produjo un comportamiento impredecible en tiempo de ejecución. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2228 en su lugar.

   ```Output
    error C2228: left of '.operator type' must have class/struct/union
   ```

   Ejemplo (antes)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
   ```

   Ejemplo (después)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
         bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
   ```

- **Nombre de tipo redundante en especificadores de tipo elaborados** Las versiones anteriores del compilador permitieron **typename** en especificadores de tipo elaborados; el código escrito de este modo es incorrecto semánticamente. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C3406 en su lugar.

   ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
   ```

   Ejemplo (antes)

   ```cpp
    template <typename class T>
    class container;
   ```

   Ejemplo (después)

   ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
   ```

- **Deducción de tipo de matrices desde una lista de inicializadores** Las versiones anteriores del compilador no admitían la deducción de tipos de matrices de una lista de inicializadores. El compilador admite ahora esta forma de deducción de tipos y, como resultado, las llamadas a las plantillas de función mediante listas de inicializadores podrían ser ahora ambiguas o se podría elegir una sobrecarga diferente de la de versiones anteriores del compilador. Para resolver estos problemas, el programa debe especificar ahora explícitamente la sobrecarga que el programador tiene como objetivo.

   Cuando este comportamiento nuevo haga que la resolución de sobrecarga considere que un candidato adicional sea igual de bueno que el candidato histórico, la llamada pasará a ser ambigua y el compilador emitirá el error del compilador C2668 como resultado.

   ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
   ```

   Ejemplo 1: llamada ambigua a una función sobrecargada (antes)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
        f({3});  error C2668: 'f' ambiguous call to overloaded function
    }
   ```

   Ejemplo 1: llamada ambigua a una función sobrecargada (después)

   ```cpp
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
   ```

   Cuando este comportamiento nuevo provoque que la resolución de sobrecarga considere que un candidato adicional es una coincidencia mejor que el candidato histórico, la llamada resuelve sin ambigüedades al nuevo candidato, provocando un cambio en el comportamiento del programa que probablemente sea diferente de lo que el programador pensaba.

   Ejemplo 2: cambio en la resolución de sobrecarga (antes)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
        f({1, 2});
    }
   ```

   Ejemplo 2: cambio en la resolución de sobrecarga (después)

   ```cpp
    struct S;  // as before

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{1, 2});
    }
   ```

- **Restauración de las advertencias de la instrucción switch**

   Una versión anterior del compilador quitó advertencias existentes anteriormente relacionadas con instrucciones **switch**; estas advertencias se han restaurado ahora. El compilador emite ahora las advertencias restauradas y se emiten ahora advertencias relacionadas con los casos específicos (incluido el caso predeterminado) en la línea que contiene el caso que genera el error, en lugar de en la última línea de la instrucción switch. Como resultado de emitir ahora esas advertencias en líneas diferentes a como se hacía en el pasado, ya no se podrán suprimir según lo previsto las advertencias suprimidas anteriormente mediante `#pragma warning(disable:####)` . Para suprimir estas advertencias según lo previsto, es posible que sea necesario mover la directiva `#pragma warning(disable:####)` a una línea por encima del primer caso que genera potencialmente el error. Las siguientes son las advertencias restauradas.

   ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
   ```

   ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
   ```

   ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
   ```

   ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
   ```

   ```Output
    warning C4064: switch of incomplete enum 'flags'
   ```

   ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
   ```

   ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
   ```

   ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
   ```

   Ejemplo de C4063: (antes)

   ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // warning C4063
            break;
        }
    };
   ```

   Ejemplo de C4063: (después)

   ```cpp
    class settings {...};  // as above

    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type<settings::flags>::type flags_t;

        auto val = settings::bit1;

        switch (static_cast<flags_t>(val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
   ```

   En su documentación se ofrecen ejemplos de las otras advertencias restauradas.

- **#include: uso del especificador de principal-directorio '..' en pathname** (solo afecta a `/Wall` `/WX`)

     Las versiones anteriores del compilador no detectaron el uso del especificador de principal-directorio '..' en el nombre de la ruta de acceso de las directivas  `#include` . El código escrito de este modo normalmente está pensado para incluir encabezados que existen fuera del proyecto usando incorrectamente rutas de acceso relativas del proyecto. Este comportamiento antiguo crea un riesgo de que el programa se pueda compilar incluyendo un archivo de origen diferente del que pensaba el programador, o que esas rutas de acceso relativas no son portables a otros entornos de compilación. Ahora el compilador detecta y notifica al programador del código escrito de esta manera y emite una advertencia C4464 de compilador opcional, si se habilita.

   ```Output
    warning C4464: relative include path contains '..'
   ```

   Ejemplo (antes)

   ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
   ```

   Ejemplo (después)

   ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
   ```

   Además, aunque el compilador no ofrece un diagnóstico específico, se recomienda no usar el especificador de directorio principal “..” para especificar los directorios de inclusión del proyecto.

- **optimize() #pragma se extiende más allá del final del archivo de encabezado** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador no detectaban cambios en la configuración de la marca de optimización que eluden un archivo de encabezado incluido dentro de una unidad de traducción. Ahora el compilador detecta y notifica al programador del código escrito de esta manera y emite una advertencia C4426 de compilador opcional en la ubicación de `#include`que genera el problema, si se habilita. Esta advertencia solo se emite si el cambio entra en conflicto con las marcas de optimización establecidas por los argumentos de la línea de comandos para el compilador.

   ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
   ```

   Ejemplo (antes)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
   ```

   Ejemplo (después)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
   ```

- **Error de coincidencia de #pragma warning(push)** y **#pragma warning(pop)** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador no detectaban que los cambios de estado `#pragma warning(push)` se emparejaban con cambios de estado `#pragma warning(pop)` en un archivo de código fuente diferente, lo que rara vez es lo previsto. Este comportamiento antiguo creaba un riesgo de que el programa se compilara con un conjunto de advertencias habilitadas diferentes de lo que el programador había pensado, lo cual puede provocar un comportamiento en tiempo de ejecución incorrecto silencioso. Ahora el compilador detecta el código escrito de esta manera, lo notifica al programador y emite una advertencia del compilador opcional C5031 en la ubicación de `#pragma warning(pop)` coincidente, si se habilita. Esta advertencia incluye una nota que hace referencia a la ubicación de `#pragma warning(push)` correspondiente.

   ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
   ```

   Ejemplo (antes)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
   ```

   Ejemplo (después)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
   ```

   Aunque es poco frecuente, a veces el código escrito de este modo es intencionado. El código escrito de este modo es sensible a los cambios en el orden de `#include`. Cuando sea posible, se recomienda que los archivos de código fuente administren el estado de advertencia de forma independiente.

- **#pragma warning(push) sin coincidencia** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador no detectaron cambios de estado `#pragma warning(push)` sin coincidencia al final de una unidad de traducción. Ahora el compilador detecta el código escrito de esta manera, lo notifica al programador y emite una advertencia del compilador opcional C5032 en la ubicación de `#pragma warning(push)` no coincidente, si se habilita. Esta advertencia solo se emite si no hay ningún error de compilación en la unidad de traducción.

   ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
   ```

   Ejemplo (antes)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
   ```

   Ejemplo (después)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
   ```

- **Se pueden emitir advertencias adicionales como resultado del seguimiento del estado de advertencia #pragma mejorado**

   Las versiones anteriores del compilador no realizaron un seguimiento de los cambios de estados `#pragma warning` lo suficientemente bueno como para emitir todas las advertencias que se pretendían. Este comportamiento provocó un riesgo de que se suprimirían algunas advertencias de manera eficaz en circunstancias diferentes de las que tenía previstas el programador. El compilador realiza ahora el seguimiento del estado `#pragma warning` con mayor eficacia, especialmente en relación con los cambios de estado `#pragma warning` dentro de las plantillas y, opcionalmente, emite nuevas advertencias C5031 y C5032 que están pensadas para ayudar al programador a localizar usos imprevistos de `#pragma warning(push)` y `#pragma warning(pop)`.

   Como resultado del seguimiento del cambio de estado de `#pragma warning` mejorado, es posible emitir ahora las advertencias anteriormente suprimidas de manera incorrecta o las advertencias relacionadas con problemas que anteriormente tenían un mal diagnóstico.

- **Mejora de la identificación del código inaccesible**

   Los cambios en la biblioteca estándar de C++ y la mejora en la capacidad para llamadas a funciones insertadas respecto a versiones anteriores del compilador pueden permitirle a este demostrar que determinado código ahora es inaccesible. Este nuevo comportamiento puede producir nuevas instancias de advertencia C4720 emitidas con mayor frecuencia.

   ```Output
    warning C4720: unreachable code
   ```

   En muchos casos, esta advertencia solo se puede emitir al compilar con las optimizaciones habilitadas, puesto que las optimizaciones pueden insertar más llamadas a funciones, eliminar código redundante o hacer posible de otra manera que se determine cierto código que no sea accesible. Hemos observado que las instancias nuevas de la advertencia C4720 han aparecido con frecuencia en bloques **try/catch**, especialmente en relación con el uso de [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

   Ejemplo (antes)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // ok
    }
   ```

   Ejemplo (después)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // warning C4702: unreachable code
    }
   ```

### <a name="VS_Update2"></a> Mejoras de conformidad en Visual Studio 2015 Update 2

- **Puede que se generen errores y advertencias adicionales como resultado de la compatibilidad parcial con la expresión SFINAE**

   Las versiones anteriores del compilador no analizaban determinados tipos de expresiones dentro de especificadores **decltype** debido a la falta de compatibilidad con la expresión SFINAE. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. Ahora, el compilador analiza estas expresiones y tiene compatibilidad parcial para la expresión SFINAE gracias a las mejoras de cumplimiento continuas. Como resultado, ahora, el compilador genera advertencias y errores detectados en las expresiones que las versiones anteriores del compilador no analizaban.

   Cuando este comportamiento nuevo analiza una expresión **decltype** que incluye un tipo que aún no se ha declarado, el compilador genera el error del compilador C2039 como resultado.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   Ejemplo 1: uso de un tipo no declarado (antes)

   ```cpp
    struct s1
    {
      template <typename T>
      auto f() -> decltype(s2<T>::type::f());  // error C2039

      template<typename>
      struct s2 {};
    }
   ```

   Ejemplo 1 (después)

   ```cpp
    struct s1
    {
      template <typename>  // forward declare s2struct s2;

      template <typename T>
      auto f() -> decltype(s2<T>::type::f());

      template<typename>
      struct s2 {};
    }
   ```

   Cuando este comportamiento nuevo analiza una expresión **decltype** en la que falta el uso necesario de la palabra clave **typename** para especificar que un nombre dependiente es un tipo, el compilador emite la advertencia del compilador C4346, junto con el error del compilador C2923.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   Ejemplo 2: un nombre dependiente no es un tipo (antes)

   ```cpp
    template <typename T>
    struct s1
    {
      typedef T type;
    };

    template <typename T>
    struct s2
    {
      typedef T type;
    };

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923
    };
   ```

   Ejemplo 2 (después)

   ```cpp
    template <typename T> struct s1 {...};  // as above
    template <typename T> struct s2 {...};  // as above

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));
    };
   ```

- Las variables de miembro `volatile`  **evitaban de forma implícita los constructores y operadores de asignación definidos** Las versiones anteriores del compilador permitían a las clases que tenían variables de miembro **volatile** que generaran automáticamente constructores para copiar o mover y operadores de asignación para copiar o mover predeterminados. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. Ahora, el compilador considera que una clase que tiene variables de miembro volátiles tiene operadores de asignación y construcción no triviales, lo que impide que se generen implementaciones predeterminadas de estos operadores automáticamente. Cuando esta clase es miembro de una unión (o una unión anónima dentro de una clase), los constructores para copiar o mover y los operadores de asignación de copiar o mover de la unión (o la clase que contiene la unión anónima) se definirán implícitamente como eliminados. Intentar crear o copiar la unión (o la clase que contiene la unión anónima) sin definirlas explícitamente es un error y, en tal caso, el compilador genera el error de compilador C2280 como resultado.

   ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
   ```

   Ejemplo (antes)

   ```cpp
    struct A
    {
      volatile int i;
      volatile int j;
    };

    extern A* pa;

    struct B
    {
      union
      {
        A a;
        int i;
      };
    };

    B b1 {*pa};
    B b2 (b1);  // error C2280
   ```

   Ejemplo (después)

   ```cpp
    struct A
    {
      int i;int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
      A a;
      a.i = pa->i;
      a.j = pa->j;
      return a;
    }

    struct B;  // as above

    B b1 {GetA()};
    B b2 (b1);  // error C2280
   ```

- **Las funciones miembro estáticas no admiten calificadores cv.**

   Las versiones anteriores de Visual C++ 2015 permitían que las funciones miembro estáticas tuvieran calificadores cv. Este comportamiento se debe a una regresión en Visual C++ 2015 y Visual C++ 2015 Update 1; Visual C++ 2013 y las versiones anteriores de Visual C++ rechazan el código escrito de este modo. El comportamiento de Visual C++ 2015 y Visual C++ 2015 Update 1 es incorrecto y no cumple el estándar de C++.  Visual Studio 2015 Update 2 rechaza el código escrito de este modo y genera el error de compilador C2511 en su lugar.

   ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
   ```

   Ejemplo (antes)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() const {}  // C2511
   ```

   Ejemplo (después)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() {}  // removed const
   ```

- **No se permite la declaración adelantada de la enumeración en el código de WinRT** (solo afecta a `/ZW`)

   El código compilado para Windows Runtime (WinRT) no permite que los tipos **enum** se declaren por adelantado, del mismo modo que cuando el código C++ administrado se compila para .NET Framework mediante el modificador de compilador `/clr`. Este comportamiento garantiza que siempre se conozca el tamaño de una enumeración y que se pueda proyectar correctamente al sistema de tipos de WinRT. El compilador rechaza el código escrito de este modo y genera los errores de compilador C2599 y C3197.

   ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
   ```

   ```Output
    error C3197: 'public': can only be used in definitions
   ```

   Ejemplo (antes)

   ```cpp
    namespace A {
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

   Ejemplo (después)

   ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

- **El operador no miembro sobrecargado new y el operador delete no se pueden declarar como inline** (nivel 1 (`/W1`), activo de manera predeterminada)

   Las versiones anteriores del compilador no generan ninguna advertencia cuando las funciones de **operador new** no miembro y de **operador delete** se declaraban como inline. El código escrito de este modo tiene un formato incorrecto (no se requiere ningún diagnóstico) y puede provocar problemas de memoria derivados de funciones operator new y operator delete no coincidentes (especialmente si se usan junto con una desasignación dimensionada) que puede resultar difícil de diagnosticar. Ahora, el compilador emite la advertencia C4595 para ayudarle a identificar el código escrito de este modo.

   ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
   ```

   Ejemplo (antes)

   ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
      ...
    }
   ```

   Ejemplo (después)

   ```cpp
    void* operator new(size_t sz)  // removed inline
    {
      ...
    }
   ```

   Corregir el código escrito de este modo puede requerir el traslado de las definiciones de operador fuera de un archivo de encabezado y al archivo de origen correspondiente.

### <a name="VS_Update3"></a> Mejoras de conformidad en Visual Studio 2015 Update 3

- **std::is_convertable ahora detecta la asignación automática** (biblioteca estándar) Las versiones anteriores del rasgo de tipo `std::is_convertable` no detectaban correctamente la asignación automática de un tipo de clase cuando el constructor de copia se había eliminado o era privado. Ahora, `std::is_convertable<>::value` está establecido de forma correcta en **false** cuando se aplica a un tipo de clase con un constructor de copias eliminado o privado.

   No hay ningún diagnóstico del compilador asociado con este cambio.

   Ejemplo

   ```cpp
    #include <type_traits>

    class X1
    {
    public:
        X1(const X1&) = delete;
    };

    class X2
    {
    private:
        X2(const X2&);
    };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
   ```

   En versiones anteriores de Visual C++, las aserciones estáticas de la parte inferior de este ejemplo se aceptaban porque `std::is_convertable<>::value` estaba establecido de forma incorrecta en **true**. Ahora, `std::is_convertable<>::value` se ha establecido de forma correcta en **false**, lo que hace que se produzcan errores en las aserciones estáticas.

- **Los constructores de copias y movimiento triviales establecidos como valor predeterminado o eliminados respetan los especificadores de acceso**

   Las versiones anteriores del compilador no comprobaban el especificador de acceso de los constructores de copias y movimiento triviales establecidos como valor predeterminado o eliminados antes de permitir llamarlos. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. En algunos casos, este comportamiento anterior ha creado un riesgo de generación de código no válido silencioso, lo que ha producido un comportamiento impredecible en tiempo de ejecución. Ahora, el compilador comprueba el especificador de acceso de los constructores de copias y movimiento triviales establecidos como valor predeterminado o eliminados para determinar si se pueden llamar y, en caso contrario, emite como resultado una advertencia del compilador C2248.

   ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
   ```

   Ejemplo (antes)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
   ```

   Ejemplo (después)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
   ```

- **Compatibilidad en desuso con código ATL con atributos**  (nivel 1 (`/W1`), activo de manera predeterminada)

   Las versiones anteriores del compilador admitían código ATL con atributos. Como parte de la fase siguiente para quitar la compatibilidad con código ATL con atributos que [comenzó en Visual C++ 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx), el código ATL con atributos está en desuso. Ahora, el compilador emite la advertencia del compilador C4467 para ayudarle a identificar este tipo de código en desuso.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Si quiere seguir usando código ATL con atributos hasta que se quite la compatibilidad del compilador, puede deshabilitar esta advertencia. Para ello, pase los argumentos de la línea de comandos `/Wv:18` o `/wd4467` al compilador o agregue `#pragma warning(disable:4467)` en el código fuente.

   Ejemplo 1 (antes)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Ejemplo 1 (después)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   A veces, necesitará o querrá crear un archivo IDL para evitar el uso de atributos ATL en desuso, como se muestra en el ejemplo de código siguiente

   Ejemplo 2 (antes)

   ```cpp
    [emitidl];
    [module(name="Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
   ```

   Primero, cree el archivo *.idl. Puede usar el archivo vc140.idl generado para obtener un archivo \*.idl que contenga las interfaces y las anotaciones.

   Después, agregue un paso MIDL a la compilación para asegurarse de que se generan las definiciones de interfaz de C++.

   Ejemplo 2 de IDL (después)

   ```cpp
    import "docobj.idl";

    [
        object,local,uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out,retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out,retval] long *pLong);
    };

    [ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
    library Foo
    {
        importlib("stdole2.tlb");
        importlib("olepro32.dll");
            [
                version(1.0),
                appobject,uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)
            ]

        coclass CFoo {
            interface ICustom;
        };
    }
   ```

   Luego, use ATL directamente en el archivo de implementación, como se muestra en el ejemplo de código siguiente.

   Ejemplo 2 de implementación (después)

   ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx<CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
        COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
   ```

- **Archivos de encabezado precompilado (PCH) y directivas #include no coincidentes** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador aceptaban directivas `#include` no coincidentes en archivos de código fuente entre compilaciones `-Yc` y `-Yu` cuando se usaban archivos de encabezado precompilado (PCH). El compilador ya no admite código escrito de este modo. Ahora, el compilador emite la advertencia del compilador CC4598 para ayudar a identificar las directivas `#include` no coincidentes cuando se usan archivos PCH.

   ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
   ```

   Ejemplo (antes):

     X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

     Z.cpp (-Yuc.h)

   ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
   ```

   Ejemplo (después)

     X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

     Z.cpp (-Yuc.h)

   ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
   ```

- **Archivos de encabezado precompilado (PCH) y directivas #include no coincidentes** (solo afecta a `/Wall` `/WX`)

   Las versiones anteriores del compilador aceptaban argumentos de la línea de comandos de directorios de inclusión no coincidentes (`-I`) en el compilador entre compilaciones `-Yc` y `-Yu` cuando se usaban archivos de encabezado precompilado (PCH). El compilador ya no admite código escrito de este modo.   Ahora, el compilador emite la advertencia del compilador CC4599 para ayudar a identificar los argumentos de la línea de comandos de directorios de inclusión no coincidentes (`-I`) cuando se usan archivos PCH.

   ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
   ```

   Ejemplo (antes)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
   ```

   Ejemplo (después)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
   ```

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Novedades para C++ en Visual Studio 2013

### <a name="improved-iso-cc-standards-support"></a>Compatibilidad mejorada de los estándares ISO C/C++

#### <a name="compiler"></a>Compilador

El Compilador de Microsoft Visual C++ admite estas características del lenguaje ISO C++11:

- Argumentos predeterminados para plantillas de funciones.
- Constructores de delegación
- Operadores de conversión explícitos.
- Listas de inicializadores e inicialización uniforme.
- Literales de cadena sin formato.
- Plantillas variádicas.
- Plantillas de alias.
- Funciones eliminadas.
- Inicializadores de miembros de datos no estáticos (NSDMI).
- Funciones establecidas como valor predeterminado. \*
- Admite estas características del lenguaje ISO C99:
- _Bool
- Literales compuestos.
- Inicializadores designados.
- Mezcla de declaraciones con código.
- La conversión de literales de cadena a valores modificables puede anularse mediante la nueva opción del compilador `/Zc:strictStrings`. En C++98, la conversión de literales de cadena a `char*` (y de literales de cadena de tipo ancho a `wchar_t*`) cayó en desuso. En C++11, la conversión se quitó completamente. Aunque el compilador podría cumplir estrictamente la norma, en su lugar se proporciona la opción `/Zc:strictStrings` para poder controlar la conversión. De forma predeterminada, esta opción está desactivada. Observe que cuando utilice esta opción en modo de depuración, STL no se compilará.
- Conversiones de referencia de rvalue/lvalue. Con las referencias rvalue, C++11 puede diferenciar claramente entre lvalues y rvalues. Anteriormente, el compilador no proporcionaba esta funcionalidad en escenarios de conversión concretos. Se ha agregado una nueva opción del compilador, `/Zc:rvalueCast`, para hacer que el compilador sea compatible con el documento de trabajo del lenguaje C++ (vea la sección 5.4, [expr.cast]/1). El comportamiento predeterminado cuando no se especifica esta opción es el mismo que en Visual Studio 2012.

> [!NOTE]
> En el caso de las funciones establecidas como valores predeterminados, no se admite el uso de =default para solicitar constructores de movimiento miembro a miembro y operadores de asignación de movimiento.

### <a name="c99-libraries"></a>Bibliotecas C99

Se han agregado declaraciones e implementaciones para las funciones que faltan en estos encabezados: math.h, ctype.h, wctype.h, stdio.h, stdlib.h y wchar.h. También se han agregado los nuevos encabezados complex.h, stdbool.h, fenv.h e inttypes.h, además de implementaciones para todas las funciones declaradas en ellos. Hay nuevos encabezados de contenedor de C++ (ccomplex, cfenv, cinttypes, ctgmath) y se han actualizado otros (ccomplex, cctype, clocale, cmath, cstdint, cstdio, cstring, cwchar y cwctype).

### <a name="standard-template-library"></a>Biblioteca de plantillas estándar

Compatibilidad con operadores de conversión explícitos de C++11, listas de inicializadores, enumeraciones con ámbito y plantillas variádicas.
Todos los contenedores admiten los requisitos específicos del elemento C++11.
Compatibilidad con estas características de C++14:

- "Objetos functor de operador transparentes" less<>, greater<>, plus<>, multiplies<>, etc.
- make_unique<T>(args...) y make_unique<T[]>(n)
- funciones no miembro cbegin()/cend(), rbegin()/rend() y crbegin()/crend().
- \<atomic> ha recibido numerosas mejoras de rendimiento.
- \<type_traits> ha recibido correcciones importantes de estabilización y código.

### <a name="breaking-changes"></a>Cambios importantes

Esta compatibilidad mejorada con las normas ISO C/C++ puede requerir cambios en el código existente para que se ajuste a C++11 y se compile correctamente en Visual C++ en Visual Studio 2013.

### <a name="visual-c-library-enhancements"></a>Mejoras de las bibliotecas de Visual C++

- Se ha agregado el SDK de REST de C++. Dispone de una implementación moderna de C++ de los servicios REST.
- Se ha mejorado la compatibilidad con la textura de C++ AMP. Ahora incluye compatibilidad con los mapas MIP y los nuevos modos de muestreo.
- Las tareas PPL admiten varias tecnologías de programación y depuración asincrónica. Las nuevas API habilitan la creación de tareas PPL tanto para resultados normales como para condiciones de excepción.

### <a name="c-application-performance"></a>Rendimiento de aplicaciones de C++

- Ahora, el vectorizador automático reconoce y optimiza más patrones de C++ para que el código se ejecute con mayor rapidez.
- Mejoras de la calidad del código de plataforma ARM y microarquitectura Atom.
- Se ha agregado la convención de llamada __vectorcall. Para usar registros vectoriales, pase los argumentos de tipo del vector con la convención de llamada __vectorcall.
- Nuevas opciones del enlazador. Los modificadores de `/Gw` (compilador) y de `/Gy` (ensamblador) permiten optimizaciones del vinculador para generar binarios más ligeros.
- La compatibilidad de memoria compartida de C++ AMP permite reducir o eliminar los procesos de copia de datos entre la CPU y la GPU.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Mejoras de optimización guiada por perfiles (PGO)

- Mejoras de rendimiento a partir de una reducción en el espacio de trabajo de aplicaciones optimizadas mediante PGO.
- Nueva Optimización guiada por perfiles para el desarrollo de aplicaciones de Windows Runtime.

### <a name="windows-runtime-app-development-support"></a>Compatibilidad con el desarrollo de aplicaciones de Windows Runtime

- **Compatibilidad con tipos a los que se aplica la conversión boxing en estructuras de valores.**

   Ahora puede definir tipos de valores utilizando campos que pueden ser null; por ejemplo, `IBox<int>^` en lugar de **int**. Esto significa que los campos pueden tener un valor o ser iguales a **nullptr**.

- **Información de excepción más completa.**

   C++/CX admite el nuevo modelo de errores de Windows que habilita la captura y la propagación de información detallada de excepciones a través de la interfaz binaria de aplicaciones (ABI); esto incluye las pilas de llamadas y las cadenas de mensaje personalizadas.

- **Object::ToString() ahora es virtual.**

   Ahora puede reemplazar ToString en tipos ref de Windows Runtime definidos por el usuario.

- **Compatibilidad con las API en desuso.**

   Las API públicas de Windows en tiempo de ejecución ahora se pueden marcar como desusadas y se puede mostrar en ellas un mensaje personalizado que aparezca como una advertencia de compilación y que proporcione directrices sobre la migración.

- **Mejoras del depurador.**

   Compatibilidad con la depuración de interoperabilidad nativa/JavaScript, diagnóstico de excepciones de Windows en tiempo de ejecución y depuración de código asincrónica (Windows en tiempo de ejecución y PPL).

> [!NOTE]
> Además de las características y mejoras específicas de C++ que se describen en esta sección, hay otras mejoras de Visual Studio que también pueden ayudarle a escribir aplicaciones de Windows Runtime más eficaces.

### <a name="diagnostics-enhancements"></a>Mejoras de diagnósticos

- Mejoras del depurador. Compatibilidad con la depuración asincrónica y la depuración Solo mi código.
- Categorías de análisis de código. Ahora puede ver el resultado por categorías desde el analizador de código, lo que le ayudará a detectar y corregir los defectos del código.
- Diagnóstico XAML. Ahora puede diagnosticar problemas relacionados con la capacidad de respuesta de la interfaz de usuario y el uso de la batería en XAML.
- Mejoras de depuración de gráficos y GPU.
- Captura remota y reproducción en dispositivos reales.
- Depuración simultánea de C++ AMP y CPU.
- Diagnósticos mejorados en tiempo de ejecución de AMP de C++.
- Depuración de seguimiento del sombreador de cálculo de HLSL.

### <a name="3-d-graphics-enhancements"></a>Mejoras de gráficos 3D

- Compatibilidad de la canalización de contenido de la imagen con el formato premultiplicado alfa DDS.
- El editor de imágenes usa el formato alfa premultiplicado para la representación y, por tanto, impide que los artefactos se representen como halos oscuros.
- Editores de imágenes y modelos. Ahora se admite la creación de filtros definidos por el usuario en el Diseñador de sombras del Editor de imágenes y el Editor de modelos.

### <a name="ide-and-productivity"></a>IDE y productividad

**Formato mejorado de código**. Puede aplicar más valores de formato al código de C++. Con esta configuración, puede controlar la colocación de llaves en una nueva línea y las palabras clave, la sangría, el espaciado y el ajuste de línea. El formato del código se aplica automáticamente cuando se completan instrucciones y bloques, y también cuando se pega código en un archivo.

**Finalización de llave.** El código de C++ ahora completa automáticamente los caracteres de cierre que se corresponden con estos caracteres de apertura:

- { (llave)
- [ (corchete)
- ( (paréntesis)
- ‘ (comilla simple)
- " (comilla doble)

**Características adicionales de finalización automática de C++.**

- Agrega un punto y coma a los tipos de clases.
- Completa los paréntesis de los literales de cadena sin formato.
- Rellena los comentarios de varias líneas (/\* \*/)

**Buscar todas las referencias** ahora resuelve automáticamente y filtra las referencias en segundo plano después de mostrar la lista de coincidencias textuales.

**Filtrado de la lista de miembros basado en contexto.** Los miembros no disponibles se excluyen de las listas de miembros de IntelliSense. Por ejemplo, los miembros privados no se muestran en la lista de miembros a menos que modifique el código que implementa el tipo. Mientras la lista de miembros está abierta, puede presionar **Ctrl**+**J** para quitar un nivel de filtrado (solo se aplica a la ventana activa de la lista de miembros). Puede presionar **Ctrl**+**J** de nuevo para quitar el filtrado textual y mostrar todos los miembros.

**Desplazamiento por la Ayuda de parámetros.** La signatura de la función que aparece en la información sobre herramientas de ayuda de parámetros ahora cambia según el número de parámetros que se han escrito realmente, en lugar de mostrar sencillamente una signatura arbitraria que no se actualizaba en función del contexto actual. La ayuda de parámetros también funciona correctamente cuando se muestra en funciones anidadas.

**Alternar archivo de encabezado/código.** Ahora puede alternar entre un encabezado y su archivo de código correspondiente mediante un comando del menú contextual o un método abreviado de teclado.

**Puede cambiarse el tamaño de la ventana Propiedades del proyecto de C++.**

**Generación automática de código del controlador de eventos en C++/CX y C++/CLI.**  Cuando escribe código para agregar un controlador de eventos en un archivo de código C++/CX o C++/CLI, el editor puede generar automáticamente la instancia de delegado y la definición de control de eventos. Cuando el código del controlador de eventos puede generarse automáticamente, aparece una ventana de información sobre herramientas.

**Mejora de Reconocimiento de ppp.** El valor Reconocimiento de ppp de los archivos del manifiesto de aplicación admite ahora el valor "Reconocimiento de ppp elevado por monitor”.

**Conmutación de configuración más rápida.** En el caso de las aplicaciones grandes, el cambio entre configuraciones (especialmente las operaciones de intercambio posteriores), se lleva a cabo mucho más rápido.

**Efectividad del tiempo de compilación.** Las numerosas optimizaciones y la utilización de varios núcleos crean compilaciones más rápidas, especialmente en proyectos grandes. Las compilaciones incrementales de las aplicaciones de C++ que tienen referencias a C++ WinMD también son mucho más rápidas.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Novedades para C++ en Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Compatibilidad mejorada con estándares de C++11

#### <a name="standard-template-library"></a>Biblioteca de plantillas estándar

- Compatibilidad con nuevos encabezados STL: \<atomic>, \<chrono>, \<condition_variable>, \<filesystem>, \<future>, \<mutex>, \<ratio> y \<thread>.
- Para optimizar la utilización de recursos de memoria, ahora los contenedores son más pequeños. Por ejemplo, en el modo de versión x86 con la configuración predeterminada, `std::vector` se ha reducido de 16 bytes en Visual Studio 2010 a 12 bytes en Visual Studio 2012 y `std::map` se ha reducido de 16 bytes en Visual Studio 2010 a 8 bytes en Visual Studio 2012.
- Tal y como permite pero no requiere el estándar de C++11, se han implementado los iteradores SCARY.

#### <a name="other-c11-enhancements"></a>Otras mejoras de C++11

- Bucles for basados en rangos. Puede escribir bucles más sólidos que funcionan con matrices, contenedores STL y colecciones de Windows Runtime con el formato for ( declaración de rango for : expresión ). Esto forma parte del lenguaje principal.
- Las expresiones lambda sin estado, que son bloques de código que comienzan con un iniciador de lambda vacío [] y no capturan ninguna variable local, ahora se pueden convertir implícitamente a punteros de función según sea necesario por el estándar de C++11.
- Compatibilidad con enumeraciones de ámbito. Ahora se admite la clave enum en la clase enum de C++. El código siguiente muestra cómo esta clave enum difiere del comportamiento anterior de enum.

   ```cpp
enum class Element { Hydrogen, Helium, Lithium, Beryllium };
void func1(Element e);
func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Compatibilidad con el desarrollo de aplicaciones de Windows Runtime

- **Modelo de interfaz de usuario basada en XAML nativo**. Para aplicaciones de Windows Runtime, puede usar el nuevo modelo de interfaz de usuario basada en XAML nativo.
- **Extensiones de componentes de Visual C++**. Estas extensiones simplifican el uso de objetos de Windows Runtime, que son una parte necesaria de las aplicaciones de Windows Runtime. Para obtener más información, consulte [Roadmap for Windows Runtime apps using C++](../windows/universal-windows-apps-cpp.md) (Guía básica para aplicaciones de Windows Runtime con C++) y [Referencia del lenguaje Visual C++ (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md).
- **Juegos de DirectX**. Ahora puede desarrollar juegos atractivos mediante la nueva compatibilidad de DirectX con aplicaciones de Windows Runtime.
- **Interoperabilidad XAML/DirectX**. Las aplicaciones de Windows Runtime que usan XAML y DirectX ahora interactúan eficazmente.
- **Desarrollo de DLL del componente de Windows Runtime**. El desarrollo de DLL del componente hace que el entorno de Windows Runtime sea extensible.

### <a name="compiler-and-linker"></a>Compilador y enlazador

- **Vectorizador automático**. El compilador analiza bucles del código y, donde sea posible, emite instrucciones que usan los registros vectoriales y las instrucciones que están presentes en todos los procesadores modernos. Esto hace que los bucles se ejecuten con mayor rapidez. (Las instrucciones del procesador se conocen como SSE, Extensiones SIMD de streaming). No es necesario habilitar o solicitar esta optimización porque se aplica automáticamente.
- **Paralelizador automático**. El compilador puede analizar bucles en el código y emitir instrucciones que propaguen los cálculos por varios núcleos o procesadores. De esta forma, los bucles se pueden ejecutar con mayor rapidez. Debe solicitar esta optimización porque no está habilitada de forma predeterminada. En muchos casos, resulta útil incluir `#pragma loop(hint_parallel(N))` en el código inmediatamente antes de los bucles que quiera paralelizar.
- El vectorizador automático y el paralelizador automático pueden trabajar juntos para que los cálculos se propaguen por varios núcleos y el código de cada núcleo use sus registros vectoriales.

### <a name="new-in-visual-studio-2012-update-1"></a>Novedades de Visual Studio 2012 Update 1

Establezca Windows XP como destino al compilar el código de C++.
Puede usar el compilador y las bibliotecas de Visual C++ para establecer como destino Windows XP y Windows Server 2003.

#### <a name="parallel-programming-support"></a>Compatibilidad con la programación en paralelo

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP acelera la ejecución del código de C++ al aprovechar las ventajas del hardware de datos en paralelo que se encuentra normalmente como una GPU en una tarjeta gráfica discreta. El modelo de programación de C++ AMP incluye matrices multidimensionales, indexación, transferencia de memoria, disposición en mosaico y una biblioteca de funciones matemáticas. Mediante el uso de restricciones de compilador y extensiones de lenguaje C++ AMP, puede controlar cómo se mueven los datos de la CPU a la GPU y viceversa.

**Depuración.** La experiencia de depuración para aplicaciones que usan C++ AMP para establecer la GPU como destino es igual que la depuración de otras aplicaciones de C++. Esto incluye las nuevas adiciones de depuración en paralelo que se mencionaron anteriormente.

**Generación de perfiles.** Ahora hay compatibilidad con la generación de perfiles para la actividad de la GPU que se basa en C++ AMP y otros modelos de programación basados en Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Mejoras generales de programación en paralelo

Con el hardware pasando a arquitecturas de núcleo múltiple y varios núcleos, los desarrolladores ya no pueden depender de las crecientes velocidades del reloj de los núcleos únicos. La compatibilidad con la programación en paralelo en el Runtime de simultaneidad permite a los desarrolladores aprovechar las ventajas de estas nuevas arquitecturas.
En Visual Studio 2010, se presentaron bibliotecas eficaces de paralelización de C++, como la biblioteca de patrones de procesamiento paralelo, junto con características para aprovechar la simultaneidad al expresar canalizaciones de flujo de datos sofisticadas. En Visual Studio 2012, estas bibliotecas se han ampliado para proporcionar un mejor rendimiento, más control y una mayor compatibilidad con los patrones de procesamiento paralelo que más necesitan los desarrolladores. La riqueza de la oferta ahora incluye:

- Un modelo de programación enriquecido basado en tareas que admite la asincronía y las continuaciones.
- Algoritmos paralelos, que admiten el paralelismo bifurcar/combinar (fork-join) (parallel_for, parallel_for con afinidad, parallel_for_each, parallel_sort, parallel_reduce, parallel_transform).
- Contenedores seguros para simultaneidad, que proporcionan versiones seguras para subprocesos de estructuras de datos std como priority_queue, queue, vector y map.
- La biblioteca de agentes asincrónicos, que los desarrolladores pueden usar para expresar canalizaciones de flujo de datos que se descomponen naturalmente en unidades simultáneas.
- Un administrador de recursos y programador personalizable para facilitar la composición fluida de los patrones de esta lista.

##### <a name="general-parallel-debugging-enhancements"></a>Mejoras generales de depuración en paralelo

Además de las ventanas **Tareas paralelas** y **Pilas paralelas**, Visual Studio 2012 ofrece una nueva ventana **Inspección paralela** para que pueda examinar los valores de una expresión en todos los procesos y subprocesos, y realizar la ordenación y el filtrado en el resultado. También puede usar sus propios visualizadores para ampliar la ventana y puede aprovechar la nueva compatibilidad con varios procesos en todas las ventanas de herramientas.

### <a name="ide"></a>IDE

**Compatibilidad con plantillas de Visual Studio.** Ahora puede usar la tecnología de Plantillas de Visual Studio para crear plantillas de elemento y proyecto de C++.

**Carga de solución asincrónica.** Ahora, los proyectos se cargan de forma asincrónica (las partes principales de la solución primero) para que pueda empezar a trabajar con mayor rapidez.

**Implementación automatizada para la depuración remota.** Se ha simplificado la implementación de archivos para la depuración remota en Visual C++. La opción **Implementar** en el menú contextual del proyecto copia automáticamente en el equipo remoto los archivos que se especifican en las propiedades de configuración de depuración. Ya no es necesario copiar los archivos manualmente en el equipo remoto.

**IntelliSense de C++/CLI.** C++/CLI ahora es totalmente compatible con IntelliSense. Las características de IntelliSense, como Información rápida, Ayuda de parámetro, Lista de miembros y Finalización automática, funcionan ahora con C++/CLI. Además, las otras mejoras de IntelliSense y del IDE que aparecen en este documento también funcionan con C++/CLI.

**Información sobre herramientas de IntelliSense con más funcionalidades.** Información rápida de IntelliSense de C++ ahora muestra información de estilo de comentarios de documentación XML más completa. Si usa una API desde una biblioteca (por ejemplo, C++ AMP) que tenga comentarios de documentación XML, la información sobre herramientas de IntelliSense muestra más información que simplemente la declaración. Además, si el código tiene los comentarios de documentación XML, la información sobre herramientas de IntelliSense mostrará la información más completa.

**Construcciones de código de C++.** El código de esqueleto está disponible para el modificador, la instrucción if-else, el bucle for y otras construcciones de código básico, en la lista desplegable Lista de miembros. Seleccione un fragmento de código de la lista para insertarlo en el código y, después, rellene la lógica necesaria. También puede crear sus propios fragmentos personalizados de código para usarlos en el editor.

**Mejoras de la lista de miembros.** La lista desplegable **Lista de miembros** aparece automáticamente al escribir código en el editor de código. Los resultados se filtran de forma que solo se muestren los miembros pertinentes a medida que escribe. Puede controlar el tipo de lógica de filtrado que usa la Lista de miembros (en el cuadro de diálogo **Opciones**, en **Editor de texto** > **C/C++** > **Avanzado**).

**Coloración semántica.** Los tipos, las enumeraciones, las macros y otros tokens de C++ ahora tienen coloración de forma predeterminada.

**Resaltado de referencia.** Al seleccionar un símbolo, ahora se resaltan todas las instancias del símbolo en el archivo actual. Presione **Ctrl**+**Mayús**+**Flecha arriba** o **Ctrl**+**Mayús**+**Flecha abajo** para desplazarse por las referencias resaltadas. Puede desactivar esta característica en el cuadro de diálogo **Opciones**, en **Editor de texto** > **C/C++** > **Avanzado**.

### <a name="application-lifecycle-management-tools"></a>Herramientas de administración del ciclo de vida de las aplicaciones

#### <a name="static-code-analysis"></a>Análisis de código estático

Se ha actualizado el análisis estático de C++ para proporcionar información de contexto de errores más completa, más reglas de análisis y mejores resultados de análisis. En la nueva ventana Análisis de código, puede filtrar mensajes por palabra clave, proyecto y gravedad. Al seleccionar un mensaje en la ventana, se resalta en el editor de código la línea en el código donde se desencadenó el mensaje. Para algunas advertencias de C++, el mensaje enumera líneas de código fuente que muestran la ruta de acceso de ejecución que genera la advertencia; se resaltan los puntos de decisión y las razones para tomar esa ruta de acceso específica.
El análisis de código se incluye en la mayoría de las ediciones de Visual Studio 2012. En las ediciones Professional, Premium y Ultimate se incluyen todas las reglas. En las ediciones Express para Windows 8 y Windows Phone, solo se incluyen las advertencias más críticas. El análisis de código no se incluye en la edición Express para Web.
Estas son algunas mejoras del análisis de código:

- Nuevas advertencias de simultaneidad que le ayudan a evitar errores de simultaneidad al asegurarse de que usa las disciplinas de bloqueo correctas en los programas de C/C++ multiproceso. El analizador detecta posibles condiciones de carrera, inversiones del orden de bloqueo, infracciones del contrato de bloqueo entre llamador y destinatario, operaciones de sincronización no coincidentes y otros errores de simultaneidad.
- Puede especificar qué reglas de C++ quiere aplicar a las ejecuciones del análisis de código mediante el uso de conjuntos de reglas.
- En la ventana **Análisis de código**, puede insertar un operador pragma en el código fuente que suprime una advertencia seleccionada.
- Puede mejorar la precisión y la integridad del análisis de código estático mediante la nueva versión del lenguaje de anotación de código fuente (SAL) de Microsoft para describir cómo una función usa sus parámetros, las suposiciones que hace sobre ellos y las garantías que hace al terminar.
- Compatibilidad con proyectos de C++ de 64 bits.

#### <a name="updated-unit-test-framework"></a>Marco de pruebas unitarias actualizado

Use el nuevo marco de pruebas unitarias de C++ en Visual Studio para escribir pruebas unitarias de C++. Agregue un nuevo proyecto de prueba unitaria a la solución existente de C++ al localizar la plantilla de proyecto de prueba unitaria de C++ en la categoría de Visual C++ en el cuadro de diálogo Nuevo proyecto. Empiece por escribir las pruebas unitarias en el código auxiliar generado TEST_METHOD en el archivo Unittest1.cpp. Cuando escriba el código de prueba, compile la solución. Si quiere ejecutar estas pruebas, abra una ventana del **Explorador de pruebas unitarias**; para ello, vaya a **Ver** > **Otras ventanas** > **Explorador de pruebas unitarias** y, después, en el menú contextual del caso de prueba que quiera, elija **Ejecutar prueba seleccionada**. Una vez que termina la serie de pruebas, puede ver los resultados de la prueba y la información adicional de seguimiento de la pila en la misma ventana.

#### <a name="architecture-dependency-graphs"></a>Gráficos de dependencias de arquitectura

Para comprender mejor el código, ahora puede generar gráficos de dependencias de los archivos binarios, de clase, espacio de nombres e inclusión de una solución. En la barra de menús, elija **Arquitectura** > **Generar gráfico de dependencias** y, después, **Para la solución** o **Para archivo de inclusión** para generar un gráfico de dependencias. Una vez completada la generación del gráfico, puede explorarlo al expandir cada nodo, obtener información sobre las relaciones de dependencia al moverse por los nodos y examinar el código fuente al elegir **Ver contenido** en el menú contextual de un nodo. Para generar un gráfico de dependencias para los archivos de inclusión, en el menú contextual de un archivo de código fuente *.cpp o archivo de encabezado *.h, elija **Generar gráfico de archivos de inclusión**.

#### <a name="architecture-explorer"></a>Explorador de arquitectura

Mediante el **Explorador de arquitectura**, puede explorar los activos de la solución, los proyectos o los archivos de C++. En la barra de menús, elija **Arquitectura** > **Ventanas** > **Explorador de arquitectura**. Puede seleccionar un nodo que le interese, por ejemplo, **Vista de clases**. En este caso, el lado derecho de la ventana de herramientas se expande con una lista de espacios de nombres. Si selecciona un espacio de nombres, una nueva columna muestra una lista de las clases, estructuras y enumeraciones de este espacio de nombres. Puede continuar explorando estos activos o volver a la columna del extremo izquierdo para iniciar otra consulta. Vea **Buscar código con el explorador de arquitectura**.

#### <a name="code-coverage"></a>Cobertura de código

La cobertura de código se ha actualizado para instrumentar binarios de forma dinámica en tiempo de ejecución. De esta forma, se reduce la sobrecarga de configuración y se proporciona un mejor rendimiento. También puede recopilar datos de cobertura de código de pruebas unitarias de aplicaciones de C++. Al crear pruebas unitarias de C++, puede usar el **Explorador de pruebas unitarias** para detectar pruebas en la solución. Para ejecutar las pruebas unitarias y recopilar datos de cobertura de código de ellas, en el **Explorador de pruebas unitarias**, elija **Analizar cobertura de código**. Puede examinar los resultados de cobertura de código en la ventana **Resultados de la cobertura de código** (en la barra de menús, elija **Prueba** > **Ventanas** > **Resultados de la cobertura de código**).

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Novedades de C++ en Visual Studio 2010

### <a name="c-compiler-and-linker"></a>Compilador y enlazador de C++

**Palabra clave auto.** La palabra clave **auto** tiene una nueva finalidad. Use la finalidad predeterminada de la palabra clave **auto** para declarar una variable cuyo tipo se deduce de la expresión de inicialización en la declaración de la variable. La opción del compilador `/Zc:auto` invoca a la nueva o a la antigua finalidad de la palabra clave **auto**.

**Especificador de tipo decltype.** El especificador de tipo **decltype** devuelve el tipo de una expresión especificada. Use el especificador de tipo **decltype** en combinación con la palabra clave **auto** para declarar un tipo complejo o que solo conoce el compilador. Por ejemplo, use la combinación para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla. O bien declare una función de plantilla llame a otra función y devuelva el tipo de valor devuelto de la función llamada.

**Expresiones lambda.** Las funciones Lambda tienen un cuerpo de función, pero no tienen nombre. Estas combinan las mejores características de los punteros de función y los objetos de función. Use una función lambda por sí misma, como un parámetro de función de plantilla en lugar de un objeto de función, o junto con la palabra clave **auto** para declarar una variable cuyo tipo es una expresión lambda.

**Referencia rvalue.** El declarador de referencia Rvalue (&&) declara una referencia para un valor rvalue. Una referencia rvalue permite usar semántica de transferencia de recursos y reenvío directo para escribir constructores, funciones y plantillas más eficientes.

**Declaración static_assert.** Una declaración **static_assert** prueba una aserción de software en tiempo de compilación, a diferencia de otros mecanismos de aserción que se prueban en tiempo de ejecución. Si se produce un error en la aserción, también se produce uno en la compilación y se emite un mensaje de error específico.

**Palabras clave nullptr y __nullptr.** El compilador de Visual C++ permite usar la palabra clave **nullptr** con código nativo o con código administrado. La palabra clave **nullptr** indica que un tipo de identificador de objeto, puntero interior o puntero nativo no apunta a un objeto. El compilador interpreta **nullptr** como código administrado al usar la opción de compilador `/clr` y como código nativo cuando no se usa la opción `/clr`.
La palabra clave **__nullptr** específica de Microsoft tiene la misma finalidad que **nullptr**, pero solo se aplica a código nativo. Si compila código nativo de C o C++ mediante la opción del compilador `/clr`, el compilador no puede determinar si la palabra clave **nullptr** es un término nativo o administrado. Para que el compilador tenga clara su intención, use la palabra clave nullptr para especificar el término administrado y **__nullptr** para especificar el término nativo.

**Opción del compilador /Zc:trigraphs.** De manera predeterminada, la compatibilidad con trígrafos está deshabilitada. Use la opción del compilador `/Zc:trigraphs` para habilitar la compatibilidad con trígrafos.
Un trígrafo se compone de dos signos de interrogación consecutivos (??) seguidos de un tercer carácter único. El compilador reemplaza un trígrafo por el carácter de puntuación correspondiente. Por ejemplo, el compilador reemplaza el trígrafo ??= por el carácter # (signo de número). Use trígrafos en archivos de código fuente de C que usen un juego de caracteres que no contenga algunos caracteres de puntuación.

**Nueva opción Optimización guiada por perfiles.** PogoSafeMode es una nueva opción de optimización guiada por perfiles que le permite especificar si se debe usar el modo seguro o el modo rápido al optimizar la aplicación. El modo seguro es seguro para subprocesos, pero es más lento que el modo rápido. El modo rápido es el comportamiento predeterminado.

**Nueva opción de Common Language Runtime (CLR) /clr:nostdlib.** Se ha agregado una nueva opción para `/clr` (compilación de Common Language Runtime). Si se incluyen varias versiones de las mismas bibliotecas, se emite un error de compilación. La nueva opción le permite excluir las bibliotecas CLR predeterminadas para que el programa pueda usar una versión especificada.

**Nueva directiva pragma detect_mismatch.** La directiva pragma detect_mismatch le permite colocar una etiqueta en los archivos que se compara con otras etiquetas que tienen el mismo nombre. Si hay varios valores para el mismo nombre, el enlazador emite un error.

**XOP intrínsecos, FMA4 intrínsecos y LWP intrínsecos.** Se han agregado nuevas funciones intrínsecas para admitir las funciones intrínsecas XOP agregadas para Visual Studio 2010 SP1, las funciones intrínsecas FMA4 agregadas para Visual Studio 2010 SP1 y las funciones intrínsecas LWP agregadas para las tecnologías de procesador de Visual Studio 2010 SP1. Use __cpuid, __cpuidex para determinar qué tecnologías de procesador son compatibles en un equipo determinado.

### <a name="visual-c-projects-and-the-build-system"></a>Proyectos de Visual C++ y el sistema de compilación

**MSBuild.** Ahora, los proyectos y las soluciones de Visual C++ se compilan con MSBuild.exe, que sustituye a VCBuild.exe. MSBuild es la misma herramienta de compilación flexible y extensible basada en XML que usan los otros lenguajes y tipos de proyecto de Visual Studio. Debido a este cambio, los archivos de proyecto de Visual C++ ahora usan un formato de archivo XML y tienen la extensión de nombre de archivo .vcxproj. Visual C++ convierte de forma automática los archivos de proyecto de versiones anteriores de Visual Studio al nuevo formato de archivo.

**Directorios de VC++.** La configuración de los directorios de VC++ ahora se encuentra en dos lugares. Use las páginas de propiedades del proyecto para establecer los valores de los directorios de VC++ de cada proyecto. Use el **Administrador de propiedades** y una hoja de propiedades para establecer los valores por configuración y globales de los directorios de VC++.

**Dependencias entre proyectos.** En versiones anteriores, las dependencias definidas entre proyectos se almacenaban en el archivo de la solución. Cuando estas soluciones se convierten al nuevo formato de archivo de proyecto, las dependencias se convierten en referencias entre proyectos. Este cambio puede afectar a las aplicaciones, ya que los conceptos de las dependencias de solución y las referencias entre proyectos son diferentes.

**Variables de entorno y macros.** La nueva macro _ITERATOR_DEBUG_LEVEL invoca compatibilidad con la depuración de los iteradores. Use esta macro en lugar de las macros anteriores _SECURE_SCL y _HAS_ITERATOR_DEBUGGING.

### <a name="visual-c-libraries"></a>Bibliotecas de Visual C++

**Bibliotecas de Runtime de simultaneidad.** El marco de Runtime de simultaneidad es compatible con las aplicaciones y los componentes que se ejecutan simultáneamente, y es el marco para programar aplicaciones simultáneas en Visual C++. Para admitir la programación de aplicaciones simultáneas, la Biblioteca de patrones de procesamiento paralelo (PPL) proporciona algoritmos y contenedores de propósito general para realizar paralelismos específicos. La Biblioteca de agentes asincrónicos proporciona un modelo de programación basado en actores e interfaces de paso de mensajes para las tareas genéricas de flujo de datos y canalización.

**Biblioteca estándar de C++.** En la siguiente lista, se describen muchos de los cambios que se han realizado en la biblioteca estándar de C++.

- Se ha usado la nueva característica de lenguaje de C++ de referencia rvalue para implementar la semántica de transferencia de recursos y el reenvío directo para muchas funciones de la biblioteca de plantillas estándar. La semántica de transferencia de recursos y el reenvío directo mejoran considerablemente el rendimiento de las operaciones que asignan variables o parámetros.
- Las referencias rvalue también se usan para implementar la nueva clase `unique_ptr`, que es un tipo de puntero inteligente más seguro que la clase `auto_ptr`. La clase `unique_ptr` se puede mover pero no copiar, implementa semántica estricta de propiedad sin afectar a la seguridad y funciona bien con contenedores que tienen en cuenta las referencias rvalue. La clase `auto_ptr` está en desuso.
- Se han agregado quince nuevas funciones, por ejemplo, `find_if_not`, `copy_if` y `is_sorted` al encabezado \<algorithm>.
- En el encabezado \<memory>, la nueva función make_shared es una manera cómoda, sólida y eficaz de realizar un puntero compartido a un objeto al mismo tiempo que se construye el objeto.
- Las listas vinculadas individualmente son compatibles con el encabezado \<forward_list>.
- Las nuevas funciones de miembro `cbegin`, `cend`, `crbegin` y `crend` proporcionan un `const_iterator` que se mueve hacia delante o hacia atrás por un contenedor.
- El encabezado \<system_error> y las plantillas relacionadas admiten el procesamiento de errores de sistema de bajo nivel. Se pueden usar los miembros de la clase `exception_ptr` para transportar excepciones entre subprocesos.
- El encabezado \<codecvt> admite la conversión de varias codificaciones de caracteres Unicode en otras codificaciones.
- El encabezado \<allocators> define varias plantillas que ayudan a asignar y liberar bloques de memoria para contenedores basados en nodos.
- Hay varias actualizaciones en el encabezado \<random>.

### <a name="microsoft-foundation-class-mfc-library"></a>Biblioteca MFC (Microsoft Foundation Class)

**Características de Windows 7.** MFC admite muchas características de Windows 7, por ejemplo, la interfaz de usuario (UI) de la cinta de opciones, la barra de tareas, las listas de accesos directos, las miniaturas con pestañas, las vistas previas en miniatura, la barra de progreso, la superposición de icono y la indexación de búsqueda. Dado que MFC admite automáticamente muchas características de Windows 7, puede que no tenga que modificar la aplicación existente. Para admitir otras características en las aplicaciones nuevas, use el Asistente para aplicaciones MFC para especificar la funcionalidad que quiera usar.

**Reconocimiento multitáctil.** MFC es compatible con las aplicaciones que tienen una interfaz de usuario multitáctil, por ejemplo, las aplicaciones escritas para el sistema operativo de Microsoft Surface. Una aplicación multitáctil puede controlar mensajes táctiles y mensajes de gestos de Windows, que son combinaciones de mensajes táctiles. Solo tiene que registrar la aplicación para eventos táctiles y de gestos, y el sistema operativo enrutará los eventos multitáctil a los controladores de eventos.

**Reconocimiento de valores altos de PPP.** De forma predeterminada, las aplicaciones MFC ahora son compatibles con valores altos de PPP. Si una aplicación es compatible con valores altos de PPP (muchos puntos por pulgada), el sistema operativo puede escalar ventanas, texto y otros elementos de la interfaz de usuario a la resolución de pantalla actual. Esto significa que es más probable que una imagen escalada se distribuya correctamente y no se muestre recortada o pixelada.

**Administrador de reinicio.** El administrador de reinicio guarda documentos automáticamente y reinicia la aplicación si se ha cerrado o se reinicia de forma inesperada. Por ejemplo, puede usar el administrador de reinicio para iniciar la aplicación después de que se cierre por una actualización automática. Para más información sobre cómo configurar la aplicación para usar el administrador de reinicio, vea **Cómo: Agregar compatibilidad con el Administrador de reinicio**.

**CTaskDialog.** La clase `CTaskDialog` se puede usar en lugar del cuadro de mensaje `AfxMessageBox` estándar. La clase `CTaskDialog` muestra y reúne más información que el cuadro de mensaje estándar.

#### <a name="safeint-library"></a>Biblioteca SafeInt

La nueva biblioteca SafeInt realiza operaciones aritméticas seguras que vigilan el desbordamiento de enteros. Esta biblioteca también compara distintos tipos de enteros.

#### <a name="new-active-template-library-atl-macros"></a>Nuevas macros de Active Template Library (ATL)

Se han agregado nuevas macros a ATL para expandir la funcionalidad de PROP_ENTRY_TYPE y PROP_ENTRY_TYPE_EX. PROP_ENTRY_INTERFACE y PROP_ENTRY_INTERFACE_EX permiten agregar una lista de CLSID válidos. PROP_ENTRY_INTERFACE_CALLBACK y PROP_ENTRY_INTERFACE_CALLBACK_EX le permiten especificar una función de devolución de llamada para determinar si un CLSID es válido.

#### <a name="analyze-warnings"></a>Advertencias /analyze

La mayoría de las advertencias `/analyze` (análisis de código de empresa) se han quitado de las bibliotecas en tiempo de ejecución de C (CRT), MFC y ATL.

#### <a name="animation-and-d2d-support"></a>Compatibilidad con animación y D2D

MFC ahora admite la animación y los gráficos de Direct2D. La biblioteca MFC contiene varias clases y funciones nuevas de MFC para admitir esta funcionalidad. También hay dos nuevos tutoriales que muestran cómo agregar un objeto D2D y un objeto de animación a un proyecto. Estos tutoriales son **Tutorial: Agregar objetos D2D a un proyecto de MFC** y **Tutorial: Agregar animación a un proyecto de MFC**.

### <a name="ide"></a>IDE

**IntelliSense mejorado.** IntelliSense para Visual C++ se ha rediseñado completamente para que sea más rápido, más preciso y capaz de manipular proyectos más grandes. Para lograr esta mejora, el IDE hace una distinción entre cómo un desarrollador ve y modifica el código fuente, y cómo el IDE usa la configuración del proyecto y el código fuente para compilar una solución.
Debido a esta separación de obligaciones, las características de exploración como **Vista de clases** y el nuevo cuadro de diálogo **Navegar a** se controlan mediante un sistema que se basa en un nuevo archivo de base de datos de escritorio (.sdf) de SQL Server que reemplaza al antiguo archivo de exploración sin compilación (.ncb). Las características de IntelliSense como Información rápida, Finalización automática y Ayuda del parámetro analizan unidades de traducción solo cuando es necesario. Las características híbridas como la nueva ventana **Jerarquía de llamadas** usan una combinación de las características de exploración e IntelliSense.
Puesto que IntelliSense solo procesa la información que necesita en el momento, el IDE tiene una mayor capacidad de respuesta. Además, dado que la información está más actualizada, las ventanas y vistas del IDE son más precisas. Por último, dado que la infraestructura del IDE está mejor organizada, tiene más capacidad y es más escalable, puede controlar proyectos más grandes.

**Errores de IntelliSense mejorado.** El IDE detecta mejor los errores que pudieron provocar una pérdida de IntelliSense y muestra un subrayado ondulado rojo debajo de ellos. Además, el IDE notifica los errores de IntelliSense en la ventana **Lista de errores**. Para mostrar el código que está causando el problema, haga doble clic en el error en la ventana **Lista de errores**.

**Característica Autocompletar de #include.** El IDE es compatible con la función Autocompletar de la palabra clave `#include`. Cuando escriba `#include`, el IDE creará un cuadro de lista desplegable de archivos de encabezado válidos. Si sigue escribiendo un nombre de archivo, el IDE filtra la lista en función de lo que escriba. En cualquier momento, puede seleccionar en la lista el archivo que quiere incluir. Esto le permite incluir rápidamente los archivos sin conocer su nombre exacto.

**Navegar a.** El cuadro de diálogo **Navegar a** le permite buscar todos los símbolos y archivos del proyecto que coinciden con una cadena especificada. Los resultados de la búsqueda se revisan inmediatamente mientras escribe caracteres adicionales en la cadena de búsqueda. El campo de comentarios **Resultados** indica el número de elementos encontrados y le ayuda a decidir si quiere restringir la búsqueda. Los campos de comentarios **Tipo o ámbito**, **Ubicación** y **Vista previa** le ayudarán a eliminar la ambigüedad de los elementos que tienen nombres similares. Además, puede extender esta característica para admitir otros lenguajes de programación.

**Depuración y generación de perfiles en paralelo.** El depurador de Visual Studio es compatible con el Runtime de simultaneidad y puede ayudarle a solucionar problemas de aplicaciones de procesamiento paralelo. Puede usar la nueva herramienta de generador de perfiles de simultaneidad para visualizar el comportamiento general de la aplicación. Además, puede usar las nuevas ventanas de herramientas para visualizar el estado de las tareas y sus pilas de llamadas.

**Diseñador de la cinta de opciones.** El **Diseñador de la cinta de opciones** es un editor gráfico que le permite crear y modificar una interfaz de usuario de la cinta de opciones de MFC. La interfaz de usuario de la cinta de opciones final se representa mediante un archivo de recursos basado en XML (.mfcribbon-ms). Para las aplicaciones existentes, puede capturar la interfaz de usuario de la cinta actual temporalmente al agregar unas pocas líneas de código y después invocar al **Diseñador de la cinta de opciones**. Después de crear el archivo de recursos de la cinta de opciones, puede reemplazar el código de la interfaz de usuario de la cinta de opciones escrito a mano con algunas instrucciones que carga el recurso de la cinta.

**Jerarquía de llamadas.** La ventana **Jerarquía de llamadas** le permite navegar a todas las funciones que se llaman mediante una función determinada o a todas las funciones que llaman a una función determinada.

### <a name="tools"></a>Herramientas

**Asistente para clases MFC.** Visual C++ 2010 trae de nuevo la estimada herramienta Asistente para clases MFC. El Asistente para clases MFC es una manera cómoda de agregar clases, mensajes y variables a un proyecto sin tener que modificar manualmente los conjuntos de archivos de código fuente.

**Asistente para controles ATL.** El Asistente para controles ATL ya no rellena automáticamente el campo `ProgID`. Si un control ATL no tiene un `ProgID`, es posible que otras herramientas no funcionen con él. Un ejemplo de una herramienta que requiere que los controles tengan un `ProgID` es el cuadro de diálogo **Insertar control ActiveX**. Para más información sobre el cuadro de diálogo, vea **Insertar control ActiveX (cuadro de diálogo)**.

### <a name="microsoft-macro-assembler-reference"></a>Referencia de Microsoft Macro Assembler

La adición del tipo de datos YMMWORD es compatible con los operandos multimedia de 256 bits que se incluyen en las instrucciones de extensiones de vector avanzadas de Intel (AVX).

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Novedades de C++ en Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Entorno de desarrollo integrado (IDE) de Visual C++

- Los cuadros de diálogo que se crean en las aplicaciones de ATL, MFC y Win32 ahora cumplen con las directrices de estilo de Windows Vista. Al crear un proyecto mediante Visual Studio 2008, todos los cuadros de diálogo que inserta en la aplicación cumplirán con las directrices de estilo de Windows Vista. Si vuelve a compilar un proyecto creado con una versión anterior de Visual Studio, los cuadros de diálogo existentes mantendrán la misma apariencia que tenían antes. Para más información sobre cómo insertar los cuadros de diálogo en la aplicación, vea **Editor de cuadros de diálogo**.

- El **Asistente para proyectos ATL** ahora tiene una opción para registrar componentes para todos los usuarios. A partir de Visual Studio 2008, los componentes COM y las bibliotecas de tipos que se crean mediante el **Asistente para proyectos ATL** se registran en el nodo HKEY_CURRENT_USER del registro a menos que seleccione **Registrar componentes para todos los usuarios**.
- El **Asistente para proyectos ATL** ya no ofrece una opción para crear proyectos ATL con atributos. A partir de Visual Studio 2008, el **Asistente para proyectos ATL** no tiene una opción para cambiar el estado con atributos de un nuevo proyecto. Todos los nuevos proyectos de ATL que crea el asistente están ahora sin atributos.
- Se puede redirigir la escritura en el Registro. Con la introducción de Windows Vista, la escritura en determinadas áreas del Registro requiere que un programa se ejecute en el modo con privilegios elevados. No es conveniente ejecutar siempre Visual Studio en este modo. La redirección por usuario redirige automáticamente las escrituras del Registro de HKEY_CLASSES_ROOT a HKEY_CURRENT_USER sin cambios de programación.
- El **Diseñador de clases** ahora tiene compatibilidad limitada con el código nativo de C++. En versiones anteriores de Visual Studio, el **Diseñador de clases** solo funcionaba con Visual C# y Visual Basic. Los usuarios de C++ ahora pueden usar el **Diseñador de clases**, pero solo en el modo de solo lectura. Para más información sobre cómo usar el **Diseñador de clases** con C++, vea **Trabajar con código de Visual C++ en el Diseñador de clases**.
- El Asistente para proyectos ya no tiene una opción para crear un proyecto de C++ SQL Server. A partir de Visual Studio 2008, el Asistente para nuevos proyectos no tiene una opción para crear un proyecto de C++ SQL Server. Los proyectos de SQL Server creados con una versión anterior de Visual Studio seguirán compilándose y funcionarán correctamente.

### <a name="visual-c-libraries"></a>Bibliotecas de Visual C++

#### <a name="general"></a>General

- Las aplicaciones pueden estar enlazadas a versiones específicas de las bibliotecas de Visual C++. A veces, una aplicación depende de las actualizaciones que se realizaron en las bibliotecas de Visual C++ después de una versión. En este caso, ejecutar la aplicación en un equipo que tiene versiones anteriores de las bibliotecas puede provocar un comportamiento inesperado. Ahora puede enlazar una aplicación a una versión específica de las bibliotecas para que no se ejecute en un equipo que tenga una versión anterior de estas.

#### <a name="stlclr-library"></a>Biblioteca STL/CLR

- Visual C++ ahora incluye la biblioteca STL/CLR. La biblioteca STL/CLR es un paquete de la biblioteca de plantillas estándar (STL), un subconjunto de la biblioteca estándar de C++, para usar con C++ y .NET Framework Common Language Runtime (CLR). Con STL/CLR, ahora puede usar todos los contenedores, iteradores y algoritmos de STL en un entorno administrado.

#### <a name="mfc-library"></a>Biblioteca MFC

- Windows Vista es compatible con los controles comunes. Se han agregado más de 150 métodos en 18 clases nuevas o existentes para admitir características en Windows Vista o para mejorar la funcionalidad de las clases MFC actuales.
- La nueva clase `CNetAddressCtrl` permite especificar y validar las direcciones IPv4 e IPv6 o los nombres DNS.
- La nueva clase `CPagerCtrl` simplifica el uso del control de paginación de Windows.
- La nueva clase `CSplitButton` simplifica el uso del control splitbutton de Windows para seleccionar una acción predeterminada u opcional.

#### <a name="c-support-library"></a>Biblioteca de compatibilidad de C++

- C++ incluye la biblioteca de serialización. La biblioteca de serialización proporciona una manera fácil y optimizada de serializar datos entre entornos nativos y administrados. La biblioteca es una alternativa a los enfoques más complejos y menos eficientes como el uso de PInvoke. Para más información, vea **Información general de la serialización en C++**.

#### <a name="atl-server"></a>Servidor ATL

- El servidor ATL se distribuye como un proyecto de código fuente compartido.
- La mayoría de la base del código del servidor ATL se ha publicado como un proyecto de código fuente compartido en CodePlex y no se instala como parte de Visual Studio 2008. Varios archivos asociados con el servidor ATL ya no forman parte de Visual Studio. Para obtener la lista de archivos quitados, vea **Removed ATL Server Files** (Archivos del servidor ATL quitados).
- Las clases de codificación y descodificación de datos de atlenc.h y las clases y funciones de utilidad de atlutil.h y atlpath.h ahora forman parte de la biblioteca ATL.
- Microsoft seguirá admitiendo las versiones del servidor ATL que se incluyen en las versiones anteriores de Visual Studio siempre que se admitan esas versiones de Visual Studio. CodePlex seguirá desarrollando el código del servidor ATL como un proyecto de la comunidad. Microsoft no es compatible con una versión de CodePlex del servidor ATL.

### <a name="visual-c-compiler-and-linker"></a>Compilador y enlazador de Visual C++

#### <a name="compiler-changes"></a>Cambios del compilador

- El compilador admite las compilaciones incrementales administradas. Al especificar esta opción, el compilador no volverá a compilar el código cuando cambie un ensamblado al que se hace referencia. En su lugar, llevará a cabo una compilación incremental. Los archivos se vuelven a compilar solo si los cambios afectan al código dependiente.
- Ya no se admiten los atributos relacionados con el servidor ATL. El compilador ya no admite varios atributos que estaban directamente relacionados con el servidor ATL. Para obtener una lista completa de los atributos quitados, vea Cambios importantes.
- El compilador admite la microarquitectura de Intel Core. El compilador contiene ajustes para la microarquitectura de Intel Core durante la generación del código. De forma predeterminada, este ajuste está activado y no se puede deshabilitar, ya que también ayuda a Pentium 4 y otros procesadores.
- Las funciones intrínsecas admiten procesadores AMD e Intel más recientes. Algunas funciones intrínsecas nuevas admiten la mayor funcionalidad en procesadores AMD e Intel más recientes. Para más información sobre las nuevas funciones intrínsecas, vea **Supplemental Streaming SIMD Extensions 3 Instructions** (Instrucciones de Extensiones SIMD de streaming 3), **Streaming SIMD Extensions 4 Instructions** (Instrucciones de Extensiones SIMD de streaming 4), **SSE4A and Advanced Bit Manipulation Intrinsics** (SSE4A y funciones intrínsecas de manipulación de bits avanzada), **AES Intrinsics** (Funciones intrínsecas de AES), **_mm_clmulepi64_si128** y **__rdtscp**.
- Se ha actualizado la función `__cpuid`. Las funciones `__cpuid` y `__cpuidex` ahora admiten varias características nuevas de las revisiones más recientes de los procesadores AMD e Intel. La función intrínseca `__cpuidex` es nueva y recopila más información de procesadores recientes.
- La opción del compilador `/MP` reduce el tiempo de compilación total. La opción `/MP` puede reducir significativamente el tiempo total para compilar varios archivos de código fuente mediante la creación de varios procesos que compilan los archivos al mismo tiempo. Esta opción es especialmente útil en equipos compatibles con hyperthreading, varios procesadores o varios núcleos.
- La opción del compilador `/Wp64` y la palabra clave **__w64** están en desuso. La opción del compilador `/Wp64` y la palabra clave **__w64**, que detecta problemas de portabilidad de 64 bits, están en desuso y se quitarán en una versión futura del compilador. En lugar de esta opción del compilador y palabra clave, use un compilador de Visual C++ que tenga una plataforma de 64 bits como destino.
- `/Qfast_transcendentals` genera código alineado para las funciones transcendentales.
- `/Qimprecise_fwaits` quita los comandos fwait internos para probar bloques al usar la opción del compilador `/fp:except`.

### <a name="linker-changes"></a>Cambios del enlazador

- El enlazador (link.exe) de Visual C++ ahora inserta la información de Control de cuentas de usuario en archivos de manifiesto para archivos ejecutables. Esta característica está habilitada de manera predeterminada. Para más información sobre cómo deshabilitar esta característica o cómo modificar el comportamiento predeterminado, vea `/MANIFESTUAC` (Insertar información de UAC en el manifiesto).
- El enlazador ahora tiene la opción `/DYNAMICBASE` para habilitar la característica de selección aleatoria del diseño del espacio de direcciones de Windows Vista. Esta opción modifica el encabezado de un archivo ejecutable para indicar si la aplicación debería fusionarse aleatoriamente mediante cambio de base en tiempo de carga.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Novedades de C++ en Visual Studio 2005

Las siguientes características eran nuevas en Visual C++ 2005 Service Pack 1:

### <a name="intrinsics-for-x86-and-x64"></a>Funciones intrínsecas para x86 y x64

- __halt
- __lidt
- __nop
- __readcr8
- __sidt
- __svm_clgi
- __svm_invlpga
- __svm_skinit
- __svm_stgi
- __svm_vmload
- __svm_vmrun
- __svm_vmsave
- __ud2
- __vmx_off
- __vmx_vmptrst
- __writecr8

### <a name="intrinsics-for-x64-only"></a>Funciones intrínsecas solo para x64

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>Nuevas palabras claves del lenguaje

__sptr, __uptr

### <a name="new-compiler-features"></a>Nuevas características del compilador

El compilador tiene cambios importantes en esta versión.

- Compiladores cruzados y nativos de 64 bits.
- Se ha agregado la opción del compilador `/analyze` (análisis de código de empresa).
- Se ha agregado la opción del compilador `/bigobj`.
- Se han agregado `/clr:pure`, `/clr:safe` y `/clr:oldSyntax`. (Las versiones posteriores están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017).
- Opciones del compilador en desuso: muchas opciones del compilador han quedado en desuso en esta versión; para más información, vea **Opciones obsoletas del compilador**.
- Se ha reducido la aplicación doble de código thunk en código `/clr`; para más información, vea **Doble thunk (C++)**.
- Ya no se pueden usar `/EH` (modelo de control de excepciones) o `/EHs` para detectar una excepción que se inicia con un valor que no sea throw; use `/EHa`.
- Se ha agregado la opción del compilador `/errorReport` (informar de los errores internos del compilador).
- Se ha agregado la opción del compilador `/favor` (optimizar para 64).
- Se ha agregado la opción del compilador `/FA`, `/Fa` (archivo de listas).
- Se ha agregado la opción del compilador `/FC` (ruta de acceso completa de archivo de código fuente en diagnósticos).
- Se ha agregado la opción del compilador `/fp` (especificar comportamiento de punto flotante).
- Se ha agregado la opción del compilador `/G` (optimizar para procesador, opciones).
- Se ha agregado la opción del compilador `/G` (optimizar para procesador, opciones).
- Se han quitado las opciones del compilador `/G3`, `/G4`, `/G5`, `/G6`, `/G7` y `/GB`. El compilador ahora usa un "modo de fusión" que intenta crear el mejor archivo de salida para todas las arquitecturas.
- Se ha quitado `/Gf`. Use `/GF` (eliminar cadenas duplicadas) en su lugar.
- `/GL` (optimización de todo el programa) ahora es compatible con `/CLRHEADER`.
- `/GR` está ahora activado de manera predeterminada.
- `/GS` (comprobación de seguridad del búfer) ahora proporciona protección de seguridad para parámetros de puntero vulnerables. `/GS` está ahora activado de manera predeterminada. Ahora, `/GS` también funciona en funciones compiladas en MSIL con `/clr` (compilación de Common Language Runtime).
- Se ha agregado la opción del compilador `/homeparams` (copiar los parámetros del Registro en la pila).
- Se ha agregado la opción del compilador `/hotpatch` (crear imagen a la que aplicar una revisión activa).
- Se ha actualizado la heurística de función insertada; vea **inline**, **__inline**, **__forceinline** e **inline_depth** para más información.
- Se han agregado muchas funciones intrínsecas nuevas y ahora se documentan muchas funciones intrínsecas que antes no estaban documentadas.
- De forma predeterminada, las llamadas a las funciones nuevas que producen un error iniciarán una excepción.
- Se han quitado las opciones del compilador `/ML` y `/MLd`. Visual C++ ya no admite la compatibilidad con la biblioteca CRT vinculada estáticamente y de un único subproceso.
- El compilador ha implementado la optimización del valor devuelto con nombre, que está habilitada cuando se compila con `/O1`, `/O2` (minimizar tamaño, maximizar velocidad), `/Og` (optimizaciones globales) y `/Ox` (optimización completa).
- Se ha quitado la opción del compilador `/Oa`, pero se omitirá de forma silenciosa; use los modificadores `noalias` o `restrict__declspec` para especificar cómo crea alias el compilador.
- Se ha quitado la opción del compilador `/Op`. Use `/fp` (especificar comportamiento de punto flotante) en su lugar.
- OpenMP ahora es compatible con Visual C++.
- Se ha agregado la opción del compilador `/openmp` (habilitar la compatibilidad con OpenMP 2.0).
- Se ha quitado la opción del compilador `/Ow`, pero se omitirá de forma silenciosa. Use los modificadores `noalias` o `restrict__declspec` para especificar cómo crea alias el compilador.

### <a name="profile-guided-optimizations"></a>Optimizaciones guiadas por perfiles

- Se ha quitado `/QI0f`.
- Se ha quitado `/QIfdiv`.
- Se ha agregado la opción del compilador `/QIPF_B` (error en la ejecución de instrucciones paso a paso de CPU en B).
- Se ha agregado la opción del compilador `/QIPF_C` (error en la ejecución de instrucciones paso a paso de CPU en C).
- Se ha agregado la opción del compilador `/QIPF_fr32` (no usar los 96 registros de punto flotante superiores).
- Se ha agregado la opción del compilador `/QIPF_noPIC` (generar código dependiente de la posición).
- Se ha agregado la opción del compilador `/QIPF_restrict_plabels` (suponer que no se crean funciones en tiempo de ejecución).

### <a name="unicode-support-in-the-compiler-and-linker"></a>Compatibilidad con Unicode en el compilador y el vinculador

- `/vd` (deshabilitar desplazamientos de constructores) ahora permite usar el operador dynamic_cast en un objeto que se está construyendo (/vd2)
- Se ha quitado la opción del compilador `/YX`. Use `/Yc` (crear archivo de encabezado precompilado) o `/Yu` (usar el archivo de encabezado precompilado) en su lugar. Si quita `/YX` de las configuraciones de compilación y no lo reemplaza por nada, puede dar lugar a compilaciones más rápidas.
- `/Zc:forScope` está ahora activado de manera predeterminada.
- `/Zc:wchar_t` está ahora activado de manera predeterminada.
- Se ha quitado la opción del compilador `/Zd`. Ya no se admite la información de depuración solo de número de línea. Use `/Zi` en su lugar [vea **/Z7, /Zi, /ZI (Formato de la información de depuración)** para más información].
- `/Zg` ahora solo es válida en archivos de código fuente de C y no en archivos de código fuente de C++.
- Se ha agregado la opción del compilador `/Zx` (depurar código optimizado para Itanium).

### <a name="new-language-features"></a>Nuevas características de lenguaje

- attributeattribute está en desuso.
- Se ha agregado el modificador `appdomain__declspec`.
- Se ha agregado la convención de llamada `__clrcall`.
- El modificador **declspec** (C++) en desuso ahora le permite especificar una cadena que se mostrará en tiempo de compilación, cuando un usuario intente acceder a una función o clase en desuso.
- El operador **dynamic_cast** tiene cambios importantes.
- Las enumeraciones nativas ahora le permiten especificar el tipo subyacente.
- Se ha agregado el modificador `jitintrinsicdeclspec`.
- Se ha agregado el modificador `noaliasdeclspec`.
- Se ha agregado el modificador `process__declspec`.
- **abstract**, **override** y **sealed** son opciones válidas para las compilaciones nativas.
- Se ha agregado la palabra clave **__restrict**.
- Se ha agregado el modificador `restrictdeclspec`.
- **__thiscall** es ahora una palabra clave.
- Ahora se documenta la palabra clave **__unaligned**.
- **volatile (C++)** ha actualizado su comportamiento con respecto a las optimizaciones.

### <a name="new-preprocessor-features"></a>Nuevas funciones del preprocesador

- Se ha agregado la macro predefinida __CLR_VER.
- La directiva pragma comment (C/C++) ahora acepta `/MANIFESTDEPENDENCY` como comentario del enlazador. La opción exestr para comentar está en desuso.
- El atributo `embedded_idl` (directiva `#import`) ahora toma un parámetro opcional.
- `fenv_access` pragma
- `float_control` pragma
- `fp_contract` pragma
- Las variables globales no se inicializarán en el orden en que se declaran si tiene variables globales en secciones pragma administradas y no administradas. Se trata de una posible novedad importante si, por ejemplo, se inicializa una variable global no administrada con variables globales administradas y se requiere un objeto administrado totalmente construido.
- Las secciones especificadas con init_seg ahora son de solo lectura y no de lectura y escritura como en las versiones anteriores.
- El valor predeterminado de inline_depth ahora es 16. Un valor predeterminado de 16 también estaba en vigor en Visual C++ .NET 2003.
- Se ha agregado la macro predefinida _INTEGRAL_MAX_BITS, vea Macros predefinidas.
- Se han agregado las macros predefinidas _M_CEE, _M_CEE_PURE y _M_CEE_SAFE, vea Macros predefinidas.
- Se ha agregado la macro predefinida _M_IX86_FP.
- Se ha agregado la macro predefinida _M_X64.
- `make_public` pragma
- Se ha actualizado la sintaxis de pragma `managed`, `unmanaged` (ahora tiene `push` y `pop`).
- Ahora, la directiva `#using` hace referencia de forma implícita a mscorlib.dll en todas las compilaciones `/clr`.
- Se ha agregado la macro predefinida _OPENMP.
- Se ha actualizado el pragma optimize, a y w ya no son parámetros válidos.
- Se ha agregado el atributo no_registry#import.
- Se han agregado los pragmas `region`, `endregion`.
- Se ha agregado la macro predefinida _VC_NODEFAULTLIB.
- Ahora se implementan macros variádicas.
- `vtordisp` está en desuso y se quitará en una próxima versión de Visual C++.
- La directiva pragma `warning` tiene ahora el especificador suppress.

### <a name="new-linker-features"></a>Nuevas características del enlazador

- Ahora se permiten los módulos (archivos de salida de MSIL de no ensamblado) como entrada al enlazador.
- Se ha agregado la opción del enlazador `/ALLOWISOLATION` (búsqueda de manifiesto).
- `/ASSEMBLYRESOURCE` (insertar un recurso administrado) se ha actualizado y ahora le permite especificar el nombre del recurso en el ensamblado, además de especificar que el recurso es privado en el ensamblado.
- Se ha agregado la opción del enlazador `/CLRIMAGETYPE` (especificar tipo de imagen CLR).
- Se ha agregado la opción del enlazador `/CLRSUPPORTLASTERROR` (conservar el último código de error para las llamadas a PInvoke).
- Se ha agregado la opción del enlazador `/CLRTHREADATTRIBUTE` (establecer el atributo del subproceso de CLR).
- Se ha agregado la opción del enlazador `/CLRUNMANAGEDCODECHECK` (agregar SupressUnmanagedCodeSecurityAttribute).
- Se ha agregado la opción del enlazador `/ERRORREPORT` (informar de los errores internos del enlazador).
- Se ha quitado la opción del enlazador `/EXETYPE`. El enlazador ya no admite la creación de controladores de dispositivos de Windows 95 y Windows 98. Use un DDK adecuado para crear estos controladores de dispositivos. La palabra clave EXETYPE ya no es válida para los archivos de definición de módulo.
- Se ha agregado la opción del enlazador `/FUNCTIONPADMIN` (crear imagen a la que aplicar una revisión activa).
- Ahora se admite la opción del enlazador `/LTCG` en módulos compilados con `/clr`. `/LTCG` también se ha actualizado para admitir las optimizaciones guiadas por perfiles.
- Se ha agregado la opción del enlazador `/MANIFEST` (crear el manifiesto del ensamblado en paralelo).
- Se ha agregado la opción del enlazador `/MANIFESTDEPENDENCY` (especificar las dependencias del manifiesto).
- Se ha agregado la opción del enlazador `/MANIFESTFILE` (nombre del archivo de manifiesto).
- Se ha quitado la opción del enlazador `/MAPINFO:LINES`.
- Se ha agregado la opción del enlazador `/NXCOMPAT` (compatible con la prevención de ejecución de datos).
- Se ha agregado la opción del enlazador `/PGD` (especificar la base de datos para las optimizaciones guiadas por perfiles).
- Se ha agregado la opción del enlazador `/PROFILE` (generador de perfiles de herramientas de rendimiento).
- La opción del enlazador `/SECTION` (especificar atributos de sección) ahora admite la negación de atributos y ya no es compatible con los atributos L o D (relacionados con VxD).
- Compatibilidad con Unicode en el compilador y el vinculador
- La opción del enlazador `/VERBOSE` (mostrar mensajes de progreso) ahora también acepta ICF y REF.
- Se ha quitado la opción del enlazador `/VXD`. El enlazador ya no admite la creación de controladores de dispositivos de Windows 95 y Windows 98. Use un DDK adecuado para crear estos controladores de dispositivos. La palabra clave VXD ya no es válida para los archivos de definición de módulo.
- Se ha quitado la opción del enlazador `/WS`. `/WS` se usaba para modificar imágenes destinadas a Windows NT 4.0. Se puede usar el nombre de archivo IMAGECFG.exe -R en lugar de `/WS`. IMAGECFG.exe se puede encontrar en el CD-ROM de Windows NT 4.0 en SUPPORT\DEBUG\I386\IMAGECFG. EXE.
- Ahora se documenta la opción del enlazador `/WX` (tratar advertencias del enlazador como errores).

### <a name="new-linker-utility-features"></a>Nuevas características de la utilidad del enlazador

- Se ha agregado la opción de editbin `/ALLOWISOLATION`.
- Se ha quitado la instrucción de archivo de definición de módulo DESCRIPTION. El enlazador ya no admite la creación de controladores de dispositivos virtuales.
- Se ha agregado la opción `/ERRORREPORT` a bscmake.exe, dumpbin.exe, editbin.exe y lib.exe.
- Se ha agregado la opción de lib `/LTCG`.
- Se ha agregado la opción de editbin `/NXCOMPAT`.
- Se ha agregado la opción de dumpbin `/RANGE`.
- Se ha agregado la opción de dumpbin `/TLS`.
- Se ha quitado la opción de editbin `/WS`. `/WS` se usaba para modificar imágenes destinadas a Windows NT 4.0. Se puede usar el nombre de archivo IMAGECFG.exe -R en lugar de `/WS`. IMAGECFG.exe se puede encontrar en el CD-ROM de Windows NT 4.0 en SUPPORT\DEBUG\I386\IMAGECFG. EXE.
- Se ha agregado la opción de lib /WX[:NO].

### <a name="new-nmake-features"></a>Nuevas características de NMAKE

- Se ha agregado `/ERRORREPORT`.
- Se ha agregado `/G`.
- Se han actualizado las reglas predefinidas.
- La macro $(MAKE), que está documentada en Macros de recursividad, ahora proporciona la ruta de acceso completa a nmake.exe.

### <a name="new-masm-features"></a>Nuevas características de MASM

- Las expresiones MASM ahora son valores de 64 bits. En versiones anteriores, las expresiones MASM eran valores de 32 bits.
- La expresión __asm int 3 ahora produce que una función se compile en código nativo.
- Ahora se documenta ALIAS (MASM).
- Se ha agregado la opción de ml.exe y ml64.exe `/ERRORREPORT`.
- Ahora se documenta .FPO.
- H2INC.exe no se distribuye en Visual C++ 2005. Si necesita seguir usando H2INC, use H2INC.exe de una versión anterior de Visual C++.
- Se ha agregado el operador IMAGEREL.
- Se ha agregado el operador HIGH32.
- Se ha agregado el operador LOW32.
- ml64.exe es una versión de MASM para la arquitectura x64. Ensambla archivos x64 de ASM en archivos objeto x64. No se admite el lenguaje de ensamblado insertado en el compilador x64. Se han agregado las siguientes directivas MASM para ml64.exe (x64):
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- .SETFRAME. Además, se ha actualizado la directiva PROC con sintaxis solo x64.
- Se ha agregado la directiva MMWORD.
- `/omf` (opción de línea de comandos de ML.exe) ahora implica `/c`. ML.exe no admite la vinculación de objetos con formato OMF.
- La directiva SEGMENT ahora es compatible con atributos adicionales.
- Se ha agregado el operador SECTIONREL.
- Se ha agregado la directiva XMMWORD.

### <a name="new-crt-features"></a>Nuevas características de CRT

- Se han agregado las versiones seguras de varias funciones. Estas funciones controlan los errores de una mejor manera y exigen controles más estrictos en los búferes para evitar errores comunes de seguridad. Las nuevas versiones seguras se identifican mediante el sufijo **_s**.
- Las versiones existentes menos seguras de muchas funciones han quedado en desuso. Para deshabilitar las advertencias sobre desuso, defina _CRT_SECURE_NO_WARNINGS.
- Ahora, muchas funciones existentes validan sus parámetros e invocan al controlador de parámetros no válidos cuando se pasa un parámetro no válido.
- Muchas funciones existentes ahora establecen `errno` donde no lo hacían antes.
- Se agregó el typedef `errno_t` con tipo entero. `errno_t` se usa siempre que un parámetro o tipo de valor devuelto de una función trate con códigos de error de `errno`. `errno_t` reemplaza a `errcode`.
- Las funciones dependientes de la configuración regional tienen ahora versiones que toman la configuración regional como un parámetro en lugar de usar la configuración regional actual. Estas nuevas funciones tienen el sufijo **_l**. Se han agregado varias funciones nuevas para trabajar con objetos de configuración regional. Las nuevas funciones incluyen `_get_current_locale`, `_create_locale` y `_free_locale`.
- Se han agregado nuevas funciones para admitir el bloqueo y desbloqueo de identificadores de archivos.
- La familia de funciones `_spawn` no restablece errno a cero si se ejecuta correctamente, como sí hacía en versiones anteriores.
- Hay disponibles versiones de la familia de funciones `printf` que le permiten especificar el orden en que se usan los argumentos.
- Unicode es ahora un formato de texto compatible. La función `_open` admite atributos _O_TEXTW, _O_UTF8 y _O_UTF16. La función `fopen` admite el método "ccs=ENCODING" para especificar un formato Unicode.
- Hay disponible una nueva versión del código administrado integrado (MSIL) de las bibliotecas CRT y se usa cuando se compila con la opción `/clr` (compilación de Common Language Runtime).
- Se ha quitado _fileinfo.
- El tamaño predeterminado de `time_t` es ahora de 64 bits, que expande el rango de `time_t` y algunas de las funciones de tiempo hasta el año 3000.
- CRT admite ahora el establecimiento de la configuración regional por subproceso. Se ha agregado la función `_configthreadlocale` para admitir esta característica.
- Se han agregado las funciones `_statusfp2` y `__control87_2` para permitir el acceso y control de la palabra de control de punto flotante en los procesadores de punto flotante x87 y SSE2.
- Se han agregado las funciones `_mkgmtime` y `_mkgmtime64` para proporcionar compatibilidad con la conversión de horas (struct tm) a la hora del meridiano de Greenwich (GMT).
- Se han realizado cambios en `swprintf` y `vswprintf` para cumplir mejor con el estándar.
- Un nuevo archivo de encabezado, INTRIN.H, proporciona prototipos para algunas funciones intrínsecas.
- La función `fopen` ahora tiene un atributo N.
- La función `_open` ahora tiene un atributo _O_NOINHERIT.
- La función `atoi` ahora devuelve INT_MAX y establece `errno` en ERANGE si se produce un desbordamiento. En versiones anteriores, el comportamiento en caso de desbordamiento no estaba definido.
- Se ha implementado la compatibilidad de la familia de funciones `printf` con la salida hexadecimal de punto flotante de acuerdo con el estándar ANSI C99 mediante los especificadores de tipo de formato %a y %A.
- La familia `printf` ahora es compatible con el prefijo de tamaño "ll" (long long).
- La función `_controlfp` se ha optimizado para mejorar el rendimiento.
- Se han agregado las versiones de depuración de algunas funciones.
- Se ha agregado `_chgsignl` y `_cpysignl` (versiones long double).
- Se ha agregado el tipo `_locale_t` a la tabla de tipos.
- Se ha agregado la nueva macro `_countof` para calcular el número de elementos de una matriz.
- En cada tema de función, se ha agregado una sección de equivalentes de .NET Framework.
- Varias funciones de cadena ahora tienen la opción de truncar cadenas en lugar de producir un error cuando los búferes de salida son demasiado pequeños; vea **_TRUNCATE**.
- `_set_se_translator` ahora requiere el uso de la opción del compilador `/EHa`.
- `fpos_t` es ahora **__int64** en `/Za` (para código de C) y cuando __STDC__ se establece manualmente (para código de C++). Era **struct**.
- _CRT_DISABLE_PERFCRIT_LOCKS puede mejorar el rendimiento de E/S de programas de un único subproceso.
- Los nombres POSIX han quedado en desuso en favor de los nombres compatibles con ISO C++ (por ejemplo, use `_getch` en lugar de `getch`).
- Hay disponibles nuevos archivos .obj de opciones de vínculo para el modo puro.
- `_recalloc` combina las características de `realloc` y `calloc`.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Novedades de C++ en Visual Studio 2003

### <a name="compiler"></a>Compilador

- Información sobre cómo ejecutar una aplicación de Extensiones administradas para C++ generada con el compilador de la versión actual en una versión anterior del entorno de ejecución.
- Preguntas más frecuentes sobre las Extensiones administradas para C++.
- Se ha agregado un tutorial que muestra cómo trasladar una aplicación nativa existente para usar las Extensiones administradas para C++: Walkthrough: Porting an Existing Native C++ Application to Interoperate with .NET Framework Components (Tutorial: Trasladar una aplicación de C++ nativa existente para que interactúe con componentes de .NET Framework).
- Ahora puede crear un delegado en un método de un tipo de valor.
- La conformidad del compilador con el estándar de C++ se ha mejorado significativamente para Visual C++ .NET 2003.
- Se ha agregado la opción del compilador `/arch`.
- `/Gf` está en desuso y se quitará en la próxima versión de Visual C++.
- Se ha agregado la opción del compilador `/G7`.
- La opción del compilador `/GS` se ha mejorado para ayudar a proteger las variables locales de saturaciones directas del búfer.
- Se ha quitado la opción del compilador `/noBool`. El compilador ahora permite que **bool** aparezca solo como una palabra clave (y no un identificador) en un archivo de código fuente de C++.
- El tipo **long long** ahora está disponible como **typedef** de **__int64**. Tenga en cuenta que aún no se admite **long long** en CRT.
- La opción del compilador `/Zm` ahora especifica el límite de asignación de memoria del encabezado precompilado.
- Ahora se documenta la función intrínseca _InterlockedCompareExchange.
- Ahora se documenta la función intrínseca _InterlockedDecrement.
- Ahora se documenta la función intrínseca _InterlockedExchange.
- Ahora se documenta la función intrínseca _InterlockedExchangeAdd.
- Ahora se documenta la función intrínseca _InterlockedIncrement.
- Se ha agregado la función intrínseca _ReadWriteBarrier.

### <a name="attributes"></a>Atributos

- Ahora se documenta el atributo `implements`.

### <a name="linker-features"></a>Características del enlazador

Se han agregado los siguientes modificadores del enlazador:

- /ASSEMBLYDEBUG
- /ASSEMBLYLINKRESOURCE
- DELAYSIGN
- /KEYFILE
- /KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

Se ha agregado la directiva .SAFESEH y la opción `/safeseh` de ml.exe.

## <a name="see-also"></a>Vea también

[Guía de migración y actualización de Visual C++](visual-cpp-porting-and-upgrading-guide.md)