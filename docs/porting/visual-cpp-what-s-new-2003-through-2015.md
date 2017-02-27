---
title: Novedades de Visual C++ de 2003 a 2015 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: c6ac9fb7400bd0c37d1da5a0c6bd66ccbf7abd6c

---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Novedades de Visual C++ de 2003 a 2015

**Nota** Para obtener más información sobre Visual Studio 2017, vea [Novedades de Visual C++ en Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) y [Mejoras de conformidad de Visual C++ en Visual Studio 2017](../cpp-conformance-improvements-2017.md).

En Visual C++ 2015 y versiones posteriores, las mejoras continuas en la conformidad del compilador a veces pueden cambiar la manera en que el compilador entiende el código fuente existente. Cuando esto sucede, pueden producirse errores nuevos o diferentes durante la compilación o puede haber incluso diferencias de comportamiento en el código previamente compilado que parecía ejecutarse correctamente.  
  
 Afortunadamente, estas diferencias tienen poco o ningún efecto en la mayoría del código fuente y cuando se necesitan código fuente u otros cambios para resolver estas diferencias, las correcciones suelen ser pequeñas y sencillas. Hemos incluido muchos ejemplos de código fuente previamente aceptable que es posible que deba cambiarse *(antes)* y las revisiones para corregirlos *(después)*.  
  
 Aunque estas diferencias pueden afectar a su código fuente u otros artefactos de compilación, no afectan a la compatibilidad binaria entre actualizaciones de versiones de Visual C++. Un tipo de cambio más drástico, el *cambio importante*, puede afectar a la compatibilidad binaria, pero este tipo de alteraciones de compatibilidad binaria solo se producen entre las versiones principales de Visual C++. por ejemplo, entre Visual C++ 2013 y Visual C++ 2015. Para obtener información sobre los cambios importantes que se produjeron entre Visual C++ 2013 y Visual C++ 2015, vea [Historial de cambios en Visual C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md).  
  
-   [Mejoras de conformidad en Visual C++ 2015](#VS_RTM)  
  
-   [Mejoras de conformidad en Update 1](#VS_Update1)  
  
-   [Mejoras de conformidad en Update 2](#VS_Update2)  
  
-   [Mejoras de conformidad en Update 3](#VS_Update3)  
  
##  <a name="a-namevsrtma-conformance-improvements-in-visual-c-2015"></a><a name="VS_RTM"></a> Mejoras de conformidad en Visual C++ 2015  
  
-   /Zc:forScope- (opción)  
  
     La opción de compilador **/Zc:forScope-** está desusada y se quitará en una próxima versión.  
  
    ```  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     Esta opción solía usarse para que el código no estándar que usa las variables de bucle se pudiese usar después del punto donde, según el estándar, debería quedar fuera del ámbito. Solo era necesario al compilar con la opción /Za, ya que sin /Za, siempre se permite usar una variable de bucle for tras el final del bucle. Si no le interesa el cumplimiento de los estándares (por ejemplo, si su código no está destinado a otros compiladores), puede desactivar la opción /Za (o establecer la propiedad Deshabilitar extensiones de lenguaje en No). Si le interesa escribir código portable y compatible con los estándares, debe volver a escribir el código de modo que se ajuste a la norma. Para ello, mueva la declaración de dichas variables a un punto fuera del bucle.  
  
    ```  
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
  
-   **Opción del compilador /Zg**  
  
     La opción de compilador /Zg (generar prototipos de función) ya no está disponible. Esta opción del compilador quedó en desuso anteriormente.  
  
-   Ya no se pueden ejecutar pruebas unitarias con C++/CLI desde la línea de comandos con mstest.exe. En su lugar, use vstest.console.exe. Consulte [Opciones de la línea de comandos para VSTest.Console.exe](/devops-test-docs/test/vstest-console-exe-command-line-options).  
  
-   **Palabra clave mutable**  
  
     El especificador de clase de almacenamiento `mutable` ya no se permite en lugares donde anteriormente se compilaba sin errores. Ahora, el compilador produce el error C2071 (clase de almacenamiento no válida). Según el estándar, el especificador mutable solo puede aplicarse a los nombres de miembros de datos de clase; no puede aplicarse a los nombres declarados como const o static y tampoco para hacer referencia a los miembros.  
  
     Por ejemplo, considere el siguiente código:  
  
    ```  
    struct S {  
        mutable int &r;  
    };  
    ```  
  
     Las versiones anteriores del compilador de Visual C++ aceptaban esto, pero ahora el compilador produce el siguiente error:  
  
    ```Output  
    error C2071: 'S::r': illegal storage class  
    ```  
  
     Para corregir el error, basta con quitar la palabra clave mutable redundante.  
  
-   **char_16_t y char32_t**  
  
     Ya no puede usar `char16_t` o `char32_t` como alias en una definición de tipo (typedef), ya que estos tipos ahora se consideran integrados. Antes era habitual que los usuarios y los creadores de bibliotecas definiesen char16_t y char32_t como alias de uint16_t y uint32_t, respectivamente.  
  
    ```  
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
  
     Para actualizar el código, quite las declaraciones typedef y cambie el nombre de todos los identificadores que estén en conflicto con estos nombres.  
  
-   **Parámetros de plantilla sin tipo**  
  
     Hay determinado código que implica parámetros de plantilla sin tipo en el que ahora se comprueba la compatibilidad de tipos cuando se proporcionan argumentos de plantilla explícitos. Por ejemplo, el código siguiente se compilaba sin errores en las versiones anteriores de Visual C++.  
  
    ```  
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
  
-   **__declspec(align)**  
  
     El compilador ya no acepta `__declspec(align)` en las funciones. Esto siempre se ignoraba, pero ahora produce un error del compilador.  
  
    ```  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     Para solucionar este problema, quite `__declspec(align)` de la declaración de función. Puesto que no tenía ningún efecto, el hecho de quitarlo no cambia nada.  
  
-   **Control de excepciones**  
  
     Hay un par de cambios en el control de excepciones. En primer lugar, los objetos de excepción deben poderse copiar o mover. El código siguiente se compilaba en [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], pero no en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```  
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
  
     El problema es que el constructor de copias es privado, por lo que el objeto no se puede copiar como cuando se controla una excepción de la manera habitual. Lo mismo sucede cuando el constructor de copias se declara `explicit`.  
  
    ```  
    struct S {  
        S();  
        explicit S(const S &);  
    };  
  
    int main()  
    {  
        throw S(); // error  
    }  
  
    ```  
  
     Para actualizar el código, asegúrese de que el constructor de copias correspondiente al objeto de excepción es público y no esté marcado como `explicit`.  
  
     Para detectar una excepción por valor, también es necesario que el objeto de excepción se pueda copiar. El código siguiente se compilaba en [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], pero no en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```  
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
  
     Para solucionar este problema, cambie el tipo de parámetro de `catch` a una referencia.  
  
    ```  
    catch(D& d)  
    {  
    }  
    ```  
  
-   **Literales de cadena seguidos de macros**  
  
     El compilador ahora admite literales definidos por el usuario. En consecuencia, los literales de cadena seguidos de macros sin ningún espacio en blanco intermedio se interpretan como literales definidos por el usuario, lo que puede dar lugar a errores o resultados inesperados. Por ejemplo, en los compiladores anteriores el código siguiente se compilaba perfectamente:  
  
    ```  
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
  
     El compilador interpretaba esto como un literal de cadena “hello” seguido de una macro, expandida en “there” y, a continuación, los dos literales de cadena se concatenaban en uno solo. En [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], el compilador interpreta esto como un literal definido por el usuario, pero dado que no hay ningún literal coincidente _x definido por el usuario, produce un error.  
  
    ```  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found  
    note: Did you forget a space between the string literal and the prefix of the following string literal?  
  
    ```  
  
     Para solucionar este problema, agregue un espacio entre el literal de cadena y la macro.  
  
-   **Literales de cadena adyacentes**  
  
     Como en el caso anterior, en versiones anteriores de Visual C++ y debido a los cambios relacionados con el análisis de cadenas, los literales de cadena adyacentes (ya fueran literales de cadena de caracteres anchos o estrechos) sin ningún espacio en blanco se interpretaban como una sola cadena concatenada. En [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], ahora debe agregarse un espacio en blanco entre las dos cadenas. Por ejemplo, el código siguiente debe modificarse:  
  
    ```  
    char * str = "abc""def";  
    ```  
  
     Simplemente agregue un espacio entre las dos cadenas.  
  
    ```  
    char * str = "abc" "def";  
    ```  
  
-   **Placement new y delete**  
  
     Se ha realizado un cambio en el operador delete a fin de adaptarlo al estándar de C++14. Detalles del cambio de los estándares se pueden encontrar en la página de [desasignación de ajuste de tamaño de C++](http://isocpp.org/files/papers/n3778.html). Los cambios agregan un formulario del operador delete global que toma un parámetro de tamaño. La novedad es que si antes usaba un operador delete con la misma firma (para que se correspondiese con un operador placement new), ahora recibirá un error del compilador (C2956, que se produce en el punto donde se usa placement new, ya que es la posición en el código en la que el compilador intenta identificar un operador delete coincidente adecuado).  
  
     La función `void operator delete(void *, size_t)` era un operador placement delete correspondiente a la función placement new "void \* operator new(size_t, size_t)" en C++11. Con la desasignación con tamaño de C ++&14;, esta función de eliminación es ahora una *función de desasignación habitual* (operador delete global). Según el estándar, si el uso de placement new busca una función de eliminación correspondiente y encuentra una función de desasignación habitual, el programa tiene un formato incorrecto.  
  
     Supongamos, por ejemplo, que el código define tanto placement new como placement delete:  
  
    ```  
    void * operator new(std::size_t, std::size_t);  
    void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     El problema se produce debido a la coincidencia de las firmas de función entre un operador placement delete definido y el nuevo operador global delete con tamaño. Analice si puede usar un tipo que no sea size_t para los operadores placement new y delete.  Tenga en cuenta que el tipo de la definición de tipo size_t depende del compilador; es una definición de tipo para int sin signo en Visual C++. Una buena solución es que use un tipo enumerado como el siguiente:  
  
    ```  
    enum class my_type : size_t {};  
  
    ```  
  
     A continuación, cambie la definición de placement new y delete para usar este tipo como el segundo argumento en lugar de size_t. También es necesario que actualice las llamadas a placement new para pasar el nuevo tipo (por ejemplo, con `static_cast<my_type>` para convertir el valor entero) y que actualice la definición de new y delete para realizar la conversión al tipo entero. No es necesario utilizar una enumeración para este fin; un tipo de clase con un miembro size_t también funcionaría.  
  
     Una solución alternativa es que pueda eliminar por completo placement new. Si el código usa placement new para implementar un bloque de memoria donde el argumento placement sea el tamaño del objeto que se va a asignar o eliminar, entonces podría usarse la característica de desasignación con tamaño para reemplazar su propio código de bloque de memoria personalizado, y así deshacerse de las funciones placement y usar simplemente su propio operador delete de dos argumentos en lugar de las funciones placement.  
  
     Si no quiere actualizar su código de forma inmediata, puede recuperar el comportamiento anterior mediante la opción de compilador /Zc:sizedDealloc-. Si usa esta opción, las funciones delete de dos argumentos no existen y no se provocará un conflicto con el operador placement delete.  
  
-   **Miembros de datos de uniones**  
  
     Los miembros de datos de uniones ya no pueden tener tipos de referencia. El código siguiente se compilaba sin problemas en [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], pero produce un error en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
    ```  
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
  
-   Ahora, las uniones anónimas se ajustan mejor al estándar. Las versiones anteriores del compilador generaban un constructor y destructor explícitos para uniones anónimas. Estos se eliminan en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
    ```  
    struct S {  
      S();  
     };  
  
     union {  
      struct {  
       S s;  
      };  
     } u; // C2280  
    ```  
  
     El código anterior genera el error siguiente en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function  
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
    ```  
  
     Para resolver este problema, proporcione sus propias definiciones del constructor o del destructor.  
  
    ```  
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
  
-   **Uniones con estructuras anónimas**  
  
     Para cumplir con el estándar, el comportamiento de runtime ha cambiado para los miembros de estructuras anónimas en uniones. El constructor de miembros de estructura anónima de una unión ya no se llama implícitamente cuando se crea este tipo de unión. Además, el destructor de miembros de estructura anónima de una unión ya no se llama implícitamente cuando la unión sale del ámbito. Analice el siguiente código, en el que una unión U contiene una estructura anónima que a su vez contiene a un miembro que es una estructura con nombre S que tiene un destructor.  
  
    ```  
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
  
     En [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], se llama al constructor de S cuando se crea la unión, y se llama al destructor de S cuando se limpia la pila de la función f. Sin embargo, en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], no se llama al constructor ni al destructor. El compilador emite una advertencia sobre este cambio de comportamiento.  
  
    ```Output  
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called  
    ```  
  
     Para restaurar el comportamiento original, asigne un nombre a la estructura anónima. El comportamiento en tiempo de ejecución de las estructuras no anónima es el mismo, independientemente de la versión del compilador.  
  
    ```  
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
  
    ```  
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
  
-   **Resolución de plantilla**  
  
     Se han hecho cambios en la resolución de nombres de plantillas. En C++, al pensar en candidatos para la resolución de un nombre, puede darse el caso de que uno o más de los nombres considerados como coincidencias posibles produzcan una creación de instancias de plantilla no válida. Normalmente, estas instancias no válidas no provocan errores del compilador; este principio se conoce como SFINAE (Substitution Failure Is Not An Error).  
  
     Ahora, si SFINAE requiere que el compilador cree una instancia de la especialización de una plantilla de clase, los errores que se producen durante este proceso son errores del compilador. En versiones anteriores, el compilador omitiría esos errores. Por ejemplo, considere el siguiente código:  
  
    ```  
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
  
-   **Constructores de copias**  
  
     Tanto en [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] como en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)], el compilador genera un constructor de copias para una clase si esa clase tiene un constructor de movimiento definido por el usuario, pero ningún constructor de copias definido por el usuario. En Dev14, este constructor de copias generado implícitamente también se marca como "= delete".  
  
##  <a name="a-namevsupdate1a-conformance-improvements-in-update-1"></a><a name="VS_Update1"></a> Mejoras de conformidad en Update 1  
  
-   **Clases base virtuales privadas y herencia indirecta**  
  
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
  
    ```  
    class base;  // as above  
  
    class middle: private virtual base {};  
    class top: public virtual middle, private virtual bottom {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
    ```  
  
-   **Operador new y operador delete sobrecargados**  
  
     Las versiones anteriores del compilador permitieron que `operator new` no miembro y `operator delete` no miembro se declarasen estático y que se declararan en espacios de nombres distintos del espacio de nombres global.  Este comportamiento anterior crea un riesgo de que el programa no llame a la implementación del operador `new` o `delete` que el programador diseñó, generando un comportamiento en tiempo de ejecución incorrecto silencioso. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2323 en su lugar.  
  
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
  
     Además, aunque el compilador no ofrece un diagnóstico específico, se considera que el operador en línea nuevo está mal formado.  
  
-   **Llamada a “operator *type*()” (conversión definida por el usuario) en tipos que no son de clase**  
  
     Las versiones anteriores del compilador permitieron que se llamara 'operator *type*()' en tipos que no son de clase mientras que se les ignora en modo silencioso. Este comportamiento anterior creó un riesgo de generación de código incorrecto silencioso, lo que produjo un comportamiento impredecible en tiempo de ejecución. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2228 en su lugar.  
  
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
  
-   **Typename redundante en los especificadores de tipos elaborados**  
  
     Las versiones anteriores del compilador permitieron `typename` en especificadores de tipo elaborados; el código escrito de este modo es incorrecto semánticamente. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C3406 en su lugar.  
  
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
  
-   **Deducción de tipos de matrices de una lista de inicializadores**  
  
     Las versiones anteriores del compilador no admitían la deducción de tipos de matrices de una lista de inicializadores. El compilador admite ahora esta forma de deducción de tipos y, como resultado, las llamadas a las plantillas de función mediante listas de inicializadores podrían ser ahora ambiguas o se podría elegir una sobrecarga diferente de la de versiones anteriores del compilador. Para resolver estos problemas, el programa debe especificar ahora explícitamente la sobrecarga que el programador tiene como objetivo.  
  
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
  
-   **Restauración de las advertencias de la instrucción switch**  
  
     Una versión anterior del compilador quitó advertencias existentes anteriormente relacionadas con instrucciones `switch` ; estas advertencias se han restaurado ahora. El compilador emite ahora las advertencias restauradas y se emiten ahora advertencias relacionadas con los casos específicos (incluido el caso predeterminado) en la línea que contiene el caso que genera el error, en lugar de en la última línea de la instrucción switch. Como resultado de emitir ahora esas advertencias en líneas diferentes a como se hacía en el pasado, ya no se podrán suprimir según lo previsto las advertencias suprimidas anteriormente mediante `#pragma warning(disable:####)` . Para suprimir estas advertencias según lo previsto, es posible que sea necesario mover la directiva `#pragma warning(disable:####)` a una línea por encima del primer caso que genera potencialmente el error. Las siguientes son las advertencias restauradas.  
  
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
  
-   **#include: uso del especificador de principal-directorio'..' en pathname** (solo afecta a /WX /Wall)  
  
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
  
-   **optimize() #pragma se extiende más allá del final del archivo de encabezado** (solo afecta a /WX /Wall)  
  
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
  
-   **Mismatched #pragma warning(push)** y **#pragma warning(pop)** (solo afecta a /WX /Wall)  
  
     Las versiones anteriores del compilador no detectaban que los cambios de estado `#pragma warning(push)` se emparejaban con cambios de estado `#pragma warning(pop)` en un archivo de código fuente diferente, lo que rara vez es lo previsto. Este comportamiento antiguo creaba un riesgo de que el programa se compilara con un conjunto de advertencias habilitadas diferentes de lo que el programador había pensado, lo cual puede provocar un comportamiento en tiempo de ejecución incorrecto silencioso. Ahora el compilador detecta el código escrito de esta manera, lo notifica al programador y emite una advertencia del compilador opcional C5031 en la ubicación de `#pragma warning(pop)` coincidente, si se habilita. Esta advertencia incluye una nota que hace referencia a la ubicación de #pragma warning(push) correspondiente.  
  
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
  
-   **#pragma warning(push) sin coincidencia** (solo afecta a /Wall /WX)  
  
     Las versiones anteriores del compilador no detectaron cambios de estado `#pragma warning(push)` sin coincidencia al final de una unidad de traducción. Ahora el compilador detecta y notifica al programador del código escrito de esta manera y emite una advertencia C5032 de compilador opcional en la ubicación de #pragma warning(push) no coincidente, si se habilita. Esta advertencia solo se emite si no hay ningún error de compilación en la unidad de traducción.  
  
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
  
-   **Se pueden emitir advertencias adicionales como resultado del seguimiento del estado de advertencia #pragma mejorado**  
  
     Las versiones anteriores del compilador no realizaron un seguimiento de los cambios de estados de advertencia #pragma lo suficientemente bueno como para emitir todas las advertencias que se pretendían. Este comportamiento provocó un riesgo de que se suprimirían algunas advertencias de manera eficaz en circunstancias diferentes de las que tenía previstas el programador. El compilador realiza ahora el seguimiento del estado de advertencia #pragma con mayor eficacia, especialmente en relación con los cambios de estado de advertencia #pragma dentro de las plantillas, y opcionalmente emite nuevas advertencias C5031 y C5032 que están pensadas para ayudar al programador a localizar usos imprevistos de `#pragma warning(push)` y `#pragma warning(pop)`.  
  
     Como resultado del seguimiento del cambio de estado de advertencia de #pragma mejorado, es posible emitir ahora las advertencias anteriormente suprimidas de manera incorrecta o las advertencias relacionadas con problemas que anteriormente tenían un mal diagnóstico.  
  
-   **Mejora de la identificación del código inaccesible**  
  
     Los cambios en la biblioteca estándar de C++ y la mejora en la capacidad para llamadas a funciones insertadas respecto a versiones anteriores del compilador pueden permitirle a este demostrar que determinado código ahora es inaccesible. Este nuevo comportamiento puede producir nuevas instancias de advertencia C4720 emitidas con mayor frecuencia.  
  
    ```Output  
    warning C4720: unreachable code  
    ```  
  
     En muchos casos, esta advertencia solo se puede emitir al compilar con las optimizaciones habilitadas, puesto que las optimizaciones pueden insertar más llamadas a funciones, eliminar código redundante o hacer posible de otra manera que se determine cierto código que no sea accesible. Hemos observado que las instancias nuevas de la advertencia C4720 han aparecido con frecuencia en bloques try/catch, especialmente en relación con el uso de [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).  
  
     Ejemplo (antes)  
  
    ```cpp  
    try   
    {   
        auto iter = std::find(v.begin(), v.end(), 5);   
    }   
    catch(…)   
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
    catch(…)   
    {   
        do_something();  // warning C4702: unreachable code  
    }  
    ```  
  
##  <a name="a-namevsupdate2a-conformance-improvements-in-update-2"></a><a name="VS_Update2"></a> Mejoras de conformidad en Update 2  
  
-   **Puede que se generen errores y advertencias adicionales como resultado de la compatibilidad parcial con la expresión SFINAE**  
  
     Las versiones anteriores del compilador no analizaban determinados tipos de expresiones dentro de especificadores `decltype` debido a la falta de compatibilidad con la expresión SFINAE. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. Ahora, el compilador analiza estas expresiones y tiene compatibilidad parcial para la expresión SFINAE gracias a las mejoras de cumplimiento continuas. Como resultado, ahora, el compilador genera advertencias y errores detectados en las expresiones que las versiones anteriores del compilador no analizaban.  
  
     Cuando este comportamiento nuevo analiza una expresión `decltype` que incluye un tipo que aún no se ha declarado, el compilador genera el error del compilador C2039 como resultado.  
  
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
  
     Cuando este comportamiento nuevo analiza una expresión `decltype` en la que falta el uso necesario de la palabra clave `typename` para especificar que un nombre dependiente es un tipo, el compilador emite la advertencia del compilador C4346, junto con el error del compilador C2923.  
  
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
  
-   **Las variables de miembro `volatile` impiden los operadores de asignación y constructores definidos implícitamente**  
  
     Las versiones anteriores del compilador permitían que se generaran automáticamente constructores para copiar o mover predeterminados y operadores de asignación para copiar o mover predeterminados para una clase con variables de miembro `volatile`. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C++. Ahora, el compilador considera que una clase que tiene variables de miembro volátiles tiene operadores de asignación y construcción no triviales, lo que impide que se generen implementaciones predeterminadas de estos operadores automáticamente.  Cuando esta clase es miembro de una unión (o una unión anónima dentro de una clase), los constructores para copiar o mover y los operadores de asignación de copiar o mover de la unión (o la clase que contiene la unión anónima) se definirán implícitamente como eliminados. Intentar crear o copiar la unión (o la clase que contiene la unión anónima) sin definirlas explícitamente es un error y, en tal caso, el compilador genera el error de compilador C2280 como resultado.  
  
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
  
-   **Las funciones miembro estáticas no admiten calificadores cv.**  
  
     Las versiones anteriores de Visual C++ 2015 permitían que las funciones miembro estáticas tuvieran calificadores cv. Este comportamiento se debe a una regresión en Visual C++ 2015 y Visual C++ 2015 Update 1; Visual C++ 2013 y las versiones anteriores de Visual C++ rechazan el código escrito de este modo. El comportamiento de Visual C++ 2015 y Visual C++ 2015 Update 1 es incorrecto y no cumple el estándar de C++.  Visual Studio 2015 Update 2 rechaza el código escrito de este modo y genera el error de compilador C2511 en su lugar.  
  
    ```Output  
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'  
    ```  
  
     Ejemplo (antes)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     Ejemplo (después)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **No se permite la declaración adelantada de la enumeración en el código de WinRT** (solo afecta a /ZW)  
  
     El código compilado para Windows Runtime (WinRT) no permite que los tipos `enum` se declaren por adelantado, del mismo modo que cuando el código C++ administrado se compila para .NET Framework mediante el modificador de compilador /clr. Este comportamiento garantiza que siempre se conozca el tamaño de una enumeración y que se pueda proyectar correctamente al sistema de tipos de WinRT. El compilador rechaza el código escrito de este modo y genera los errores de compilador C2599 y C3197.  
  
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
  
-   **El operador no miembro sobrecargado new y el operador delete no se pueden declarar como inline** (nivel 1 (/W1), activo de manera predeterminada)  
  
     Las versiones anteriores del compilador no generan ninguna advertencia cuando las funciones de operador no miembro new y de operador delete se declaraban como inline. El código escrito de este modo tiene un formato incorrecto (no se requiere ningún diagnóstico) y puede provocar problemas de memoria derivados de operadores new y delete no coincidentes (especialmente si se usan junto con una desasignación dimensionada) que puede resultar difícil de diagnosticar.   Ahora, el compilador emite la advertencia C4595 para ayudarle a identificar el código escrito de este modo.  
  
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
  
##  <a name="a-namevsupdate3a-conformance-improvements-in-update-3"></a><a name="VS_Update3"></a> Mejoras de conformidad en Update 3  
  
-   **std::is_convertable ahora detecta la asignación automática** (biblioteca estándar)  
  
     Las versiones anteriores del rasgo de tipo `std::is_convertable` no detectaban correctamente la asignación automática de un tipo de clase cuando el constructor de copias se había eliminado o era privado. Ahora, `std::is_convertable<>::value` está establecido de forma correcta en `false` cuando se aplica a un tipo de clase con un constructor de copias eliminado o privado.  
  
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
  
     En versiones anteriores de Visual C++, las aserciones estáticas de la parte inferior de este ejemplo se aceptaban porque `std::is_convertable<>::value` estaba establecido de forma incorrecta en `true`. Ahora, `std::is_convertable<>::value` se ha establecido de forma correcta en `false`, lo que hace que se produzcan errores en las aserciones estáticas.  
  
-   **Los constructores de copias y movimiento triviales establecidos como valor predeterminado o eliminados respetan los especificadores de acceso**  
  
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
  
-   **Compatibilidad en desuso con código ATL con atributos ** (nivel 1 (/W1), activo de manera predeterminada)  
  
     Las versiones anteriores del compilador admitían código ATL con atributos. Como parte de la fase siguiente para quitar la compatibilidad con código ATL con atributos que [comenzó en Visual C++ 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx), el código ATL con atributos está en desuso. Ahora, el compilador emite la advertencia del compilador C4467 para ayudarle a identificar este tipo de código en desuso.  
  
    ```Output  
    warning C4467: Usage of ATL attributes is deprecated  
    ```  
  
     Si quiere seguir usando código ATL con atributos hasta que se quite la compatibilidad del compilador, puede deshabilitar esta advertencia. Para ello, pase los argumentos de la línea de comandos `/Wv:18` o `/wd:4467` al compilador o agregue `#pragma warning(disable:4467)` en el código fuente.  
  
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
  
-   **Archivos de encabezado precompilado (PCH) y directivas #include no coincidentes** (solo afecta a /Wall /WX)  
  
     Las versiones anteriores del compilador aceptaban directivas `#include` no coincidentes en archivos de código fuente entre compilaciones `-Yc` y `-Yu` cuando se usaban archivos de encabezado precompilado (PCH). El compilador ya no admite código escrito de este modo.   Ahora, el compilador emite la advertencia del compilador CC4598 para ayudar a identificar las directivas `#include` no coincidentes cuando se usan archivos PCH.  
  
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
  
-   **Archivos de encabezado precompilado (PCH) y directorios de inclusión no coincidentes** (solo afecta a /Wall /WX)  
  
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


<!--HONumber=Feb17_HO4-->


