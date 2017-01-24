---
title: "Cambios importantes en Visual C++ 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "principales cambios [C++]"
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
caps.latest.revision: 124
caps.handback.revision: 117
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cambios importantes en Visual C++ 2015
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se actualiza a una nueva versión del compilador de Visual C\+\+, se pueden producir errores de compilación o en tiempo de ejecución en código previamente compilado que se ejecutaba correctamente. Los cambios en la nueva versión que producen tales problemas se conocen como *cambios importantes* y normalmente son necesarios debido a las modificaciones en el estándar del lenguaje C\+\+, las firmas de función o la disposición de los objetos en la memoria.  
  
 Para evitar errores en tiempo de ejecución que son difíciles de detectar y diagnosticar, recomendamos que nunca vincule estáticamente los binarios compilados con versiones diferentes del compilador. Además, cuando actualice un proyecto EXE o DLL, asegúrese de actualizar las bibliotecas a las que está vinculado. Si utiliza tipos CRT \(Runtime de C\) o STL \(Biblioteca de plantillas estándar\), no los pase entre los binarios \(incluidos los archivos DLL\) que se compilaron con versiones diferentes del compilador. Para obtener más información, vea [Errores potenciales que pasan los objetos de CRT entre los límites de DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).  
  
 También se recomienda que nunca escriba código que dependa de una disposición determinada de un objeto que no sea una interfaz COM o un objeto POD. Si escribe código de esta manera, debe asegurarse de que funciona después de la actualización. Para obtener más información, vea [Portabilidad en los límites de ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md).  
  
 En el resto de este artículo se describen cambios importantes concretos en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]. En el artículo, los términos “nuevo comportamiento” o “ahora” hacen referencia a esa versión. Los términos “comportamiento anterior” y “antes” hacen referencia a Visual Studio 2013 y versiones anteriores. Para información sobre cambios adicionales en Visual Studio 2015 Update 1, vea [Cambios importantes en Update 1](../misc/breaking-changes-in-visual-cpp-2015-update-1.md).  
  
1.  [Cambios importantes en el compilador](#BK_compiler)  
  
2.  [Cambios importantes en la biblioteca en tiempo de ejecución de C \(CRT\)](#BK_CRT)  
  
3.  [Cambios importantes en la biblioteca estándar de C\+\+ y en la biblioteca de plantillas estándar \(STL\)](#BK_STL)  
  
4.  [Cambios importantes en MFC y ATL](#BK_MFC)  
  
5.  [Cambios importantes en el Runtime de simultaneidad](#BK_ConcRT)  
  
##  <a name="BK_compiler"></a> Compilador de Visual C\+\+  
  
-   \/Zc:forScope\- \(opción\)  
  
     La opción de compilador **\/Zc:forScope\-** está desusada y se quitará en una próxima versión.  
  
    ```  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     Esta opción solía usarse para que el código no estándar que usa las variables de bucle se pudiese usar después del punto donde, según el estándar, debería quedar fuera del ámbito. Solo era necesario al compilar con la opción \/Za, ya que sin \/Za, siempre se permite usar una variable de bucle for tras el final del bucle. Si no le interesa el cumplimiento de los estándares \(por ejemplo, si su código no está destinado a otros compiladores\), puede desactivar la opción \/Za \(o establecer la propiedad Deshabilitar extensiones de lenguaje en No\). Si le interesa escribir código portable y compatible con los estándares, debe volver a escribir el código de modo que se ajuste a la norma. Para ello, mueva la declaración de dichas variables a un punto fuera del bucle.  
  
    ```  
    // zc_forScope.cpp // compile with: /Zc:forScope- /Za // C2065 expected int main() { // Uncomment the following line to resolve. // int i; for (int i =0; i < 1; i++) ; i = 20;   // i has already gone out of scope under /Za }  
    ```  
  
-   **Opción del compilador \/Zg**  
  
     La opción de compilador \/Zg \(generar prototipos de función\) ya no está disponible. Esta opción del compilador quedó en desuso anteriormente.  
  
-   Ya no se pueden ejecutar pruebas unitarias con C\+\+\/CLI desde la línea de comandos con mstest.exe. En su lugar, use vstest.console.exe. Vea [Opciones de la línea de comandos para VSTest.Console.exe](../Topic/VSTest.Console.exe%20command-line%20options.md).  
  
-   **palabra clave mutable**  
  
     El especificador de clase de almacenamiento `mutable` ya no se permite en lugares donde anteriormente se compilaba sin errores. Ahora, el compilador produce el error C2071 \(clase de almacenamiento no válida\). Según el estándar, el especificador mutable solo puede aplicarse a los nombres de miembros de datos de clase; no puede aplicarse a los nombres declarados como const o static y tampoco para hacer referencia a los miembros.  
  
     Por ejemplo, considere el siguiente código:  
  
    ```  
    struct S { mutable int &r; };  
    ```  
  
     Las versiones anteriores del compilador de Visual C\+\+ aceptaban esto, pero ahora el compilador produce el siguiente error:  
  
    ```Output  
    error C2071: 'S::r': clase de almacenamiento no válida  
    ```  
  
     Para corregir el error, basta con quitar la palabra clave mutable redundante.  
  
-   **char\_16\_t and char32\_t**  
  
     Ya no puede usar `char16_t` o `char32_t` como alias en una definición de tipo \(typedef\), ya que estos tipos ahora se consideran integrados. Antes era habitual que los usuarios y los creadores de bibliotecas definiesen char16\_t y char32\_t como alias de uint16\_t y uint32\_t, respectivamente.  
  
    ```  
    #include <cstdint> typedef uint16_t char16_t; //C2628 typedef uint32_t char32_t; //C2628 int main(int argc, char* argv[]) { uint16_t x = 1; uint32_t y = 2; char16_t a = x; char32_t b = y; return 0; }  
    ```  
  
     Para actualizar el código, quite las declaraciones typedef y cambie el nombre de todos los identificadores que estén en conflicto con estos nombres.  
  
-   **Parámetros de plantilla sin tipo**  
  
     Hay determinado código que implica parámetros de plantilla sin tipo en el que ahora se comprueba la compatibilidad de tipos cuando se proporcionan argumentos de plantilla explícitos. Por ejemplo, el código siguiente se compilaba sin errores en las versiones anteriores de Visual C\+\+.  
  
    ```  
    struct S1 { void f(int); void f(int, int); }; struct S2 { template <class C, void (C::*Function)(int) const> void f() {} }; void f() { S2 s2; s2.f<S1, &S1::f>(); }  
  
    ```  
  
     El compilador actual produce correctamente un error, porque el tipo de parámetro de plantilla no coincide con el argumento de plantilla \(el parámetro es un puntero a miembro const, pero la función f no es const\):  
  
    ```Output  
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'  
    ```  
  
     Para solucionar este error en el código, asegúrese de que el tipo del argumento de la plantilla que está usando coincide con el tipo declarado del parámetro de plantilla.  
  
-   **\_\_declspec\(align\)**  
  
     El compilador ya no acepta `__declspec(align)` en las funciones. Esto siempre se ignoraba, pero ahora produce un error del compilador.  
  
    ```  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     Para solucionar este problema, quite `__declspec(align)` de la declaración de función. Puesto que no tenía ningún efecto, el hecho de quitarlo no cambia nada.  
  
-   **Control de excepciones**  
  
     Hay un par de cambios en el control de excepciones. En primer lugar, los objetos de excepción deben poderse copiar o mover. El código siguiente se compilaba en [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], pero no en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```  
    struct S { public: S(); private: S(const S &); }; int main() { throw S(); // error }  
  
    ```  
  
     El problema es que el constructor de copias es privado, por lo que el objeto no se puede copiar como cuando se controla una excepción de la manera habitual. Lo mismo sucede cuando el constructor de copias se declara `explicit`.  
  
    ```  
    struct S { S(); explicit S(const S &); }; int main() { throw S(); // error }  
  
    ```  
  
     Para actualizar el código, asegúrese de que el constructor de copias correspondiente al objeto de excepción es público y no esté marcado como `explicit`.  
  
     Para detectar una excepción por valor, también es necesario que el objeto de excepción se pueda copiar. El código siguiente se compilaba en [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], pero no en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```  
    struct B { public: B(); private: B(const B &); }; struct D : public B { }; int main() { try { } catch (D d) // error { } }  
  
    ```  
  
     Para solucionar este problema, cambie el tipo de parámetro de `catch` a una referencia.  
  
    ```  
    catch(D& d) { }  
    ```  
  
-   **Literales de cadena seguidos de macros**  
  
     El compilador ahora admite literales definidos por el usuario. En consecuencia, los literales de cadena seguidos de macros sin ningún espacio en blanco intermedio se interpretan como literales definidos por el usuario, lo que puede dar lugar a errores o resultados inesperados. Por ejemplo, en los compiladores anteriores el código siguiente se compilaba perfectamente:  
  
    ```  
    #define _x "there" char* func() { return "hello"_x; } int main() { char * p = func(); return 0; }  
    ```  
  
     El compilador interpretaba esto como un literal de cadena “hello” seguido de una macro, expandida en “there” y, a continuación, los dos literales de cadena se concatenaban en uno solo. En [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], el compilador interpreta esto como un literal definido por el usuario, pero dado que no hay ningún literal coincidente \_x definido por el usuario, produce un error.  
  
    ```  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found note: Did you forget a space between the string literal and the prefix of the following string literal?  
  
    ```  
  
     Para solucionar este problema, agregue un espacio entre el literal de cadena y la macro.  
  
-   **Literales de cadena adyacentes**  
  
     Como en el caso anterior, en versiones anteriores de Visual C\+\+ y debido a los cambios relacionados con el análisis de cadenas, los literales de cadena adyacentes \(ya fueran literales de cadena de caracteres anchos o estrechos\) sin ningún espacio en blanco se interpretaban como una sola cadena concatenada. En [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], ahora debe agregarse un espacio en blanco entre las dos cadenas. Por ejemplo, el código siguiente debe modificarse:  
  
    ```  
    char * str = "abc""def";  
    ```  
  
     Simplemente agregue un espacio entre las dos cadenas.  
  
    ```  
    char * str = "abc" "def";  
    ```  
  
-   **Nuevo placement delete**  
  
     Se ha realizado un cambio en el operador delete a fin de adaptarlo al estándar de C\+\+14. Detalles del cambio de los estándares se pueden encontrar en la página de [desasignación de ajuste de tamaño de C\+\+](http://isocpp.org/files/papers/n3778.html). Los cambios agregan un formulario del operador delete global que toma un parámetro de tamaño. La novedad es que si antes usaba un operador delete con la misma firma \(para que se correspondiese con un operador placement new\), ahora recibirá un error del compilador \(C2956, que se produce en el punto donde se usa placement new, ya que es la posición en el código en la que el compilador intenta identificar un operador delete coincidente adecuado\).  
  
     La función `void operator delete(void *, size_t)` era un operador placement delete correspondiente a la función placement new “void \* operator new\(size\_t, size\_t\)” en C\+\+11. Con la desasignación con tamaño de C \+\+ 14, esta función de eliminación es ahora una *función de desasignación habitual* \(operador delete global\). Según el estándar, si el uso de placement new busca una función de eliminación correspondiente y encuentra una función de desasignación habitual, el programa tiene un formato incorrecto.  
  
     Supongamos, por ejemplo, que el código define tanto placement new como placement delete:  
  
    ```  
    void * operator new(std::size_t, std::size_t); void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     El problema se produce debido a la coincidencia de las firmas de función entre un operador placement delete definido y el nuevo operador global delete con tamaño. Analice si puede usar un tipo que no sea size\_t para los operadores placement new y delete.  Tenga en cuenta que el tipo de la definición de tipo size\_t depende del compilador; es una definición de tipo para int sin signo en Visual C\+\+. Una buena solución es que use un tipo enumerado como el siguiente:  
  
    ```  
    enum class my_type : size_t {};  
  
    ```  
  
     A continuación, cambie la definición de placement new y delete para usar este tipo como el segundo argumento en lugar de size\_t. También es necesario que actualice las llamadas a placement new para pasar el nuevo tipo \(por ejemplo, con `static_cast<my_type>` para convertir el valor entero\) y que actualice la definición de new y delete para realizar la conversión al tipo entero. No es necesario utilizar una enumeración para este fin; un tipo de clase con un miembro size\_t también funcionaría.  
  
     Una solución alternativa es que pueda eliminar por completo placement new. Si el código usa placement new para implementar un bloque de memoria donde el argumento placement sea el tamaño del objeto que se va a asignar o eliminar, entonces podría usarse la característica de desasignación con tamaño para reemplazar su propio código de bloque de memoria personalizado, y así deshacerse de las funciones placement y usar simplemente su propio operador delete de dos argumentos en lugar de las funciones placement.  
  
     Si no quiere actualizar su código de forma inmediata, puede recuperar el comportamiento anterior mediante la opción de compilador \/Zc:sizedDealloc\-. Si usa esta opción, las funciones delete de dos argumentos no existen y no se provocará un conflicto con el operador placement delete.  
  
-   **Miembros de datos de uniones**  
  
     Los miembros de datos de uniones ya no pueden tener tipos de referencia. El código siguiente se compilaba sin problemas en [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], pero produce un error en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
    ```  
    union U1 { const int i; }; union U2 { int &i; }; union U3 { struct {int &i;}; };  
    ```  
  
     El código anterior produce los errores siguientes:  
  
    ```Output  
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type  
    ```  
  
     Para solucionar este problema, cambie los tipos de referencia a un puntero o a un valor. Para poder cambiar el tipo a un puntero, hay que hacer cambios en el código que usa el campo union. Si se cambia el código a un valor, también cambian los datos almacenados en la unión, lo que afecta a otros campos, ya que los campos de tipos union comparten la misma memoria. En función del tamaño del valor, también podrá cambiar el tamaño de la unión.  
  
-   Ahora, las uniones anónimas se ajustan mejor al estándar. Las versiones anteriores del compilador generaban un constructor y destructor explícitos para uniones anónimas. Estos se eliminan en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
    ```  
    struct S { S(); }; union { struct { S s; }; } u; // C2280  
    ```  
  
     El código anterior genera el error siguiente en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
    ```  
  
     Para resolver este problema, proporcione sus propias definiciones del constructor o del destructor.  
  
    ```  
    struct S { // Provide a default constructor by adding an empty function body. S() {} }; union { struct { S s; }; } u;  
    ```  
  
-   **Uniones con estructuras anónimas**  
  
     Para cumplir con el estándar, el comportamiento de runtime ha cambiado para los miembros de estructuras anónimas en uniones. El constructor de miembros de estructura anónima de una unión ya no se llama implícitamente cuando se crea este tipo de unión. Además, el destructor de miembros de estructura anónima de una unión ya no se llama implícitamente cuando la unión sale del ámbito. Analice el siguiente código, en el que una unión U contiene una estructura anónima que a su vez contiene a un miembro que es una estructura con nombre S que tiene un destructor.  
  
    ```  
    #include <stdio.h> struct S { S() { printf("Creating S\n"); } ~S(){ printf("Destroying S\n"); } }; union U { struct { S s; }; U() {} ~U(){} }; void f() { U u; // Destructor implicitly called here. } int main() { f(); char s[1024]; printf("Press any key.\n"); gets_s(s); return 0; }  
    ```  
  
     En [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], se llama al constructor de S cuando se crea la unión, y se llama al destructor de S cuando se limpia la pila de la función f. Sin embargo, en [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], no se llama al constructor ni al destructor. El compilador emite una advertencia sobre este cambio de comportamiento.  
  
    ```Output  
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called  
    ```  
  
     Para restaurar el comportamiento original, asigne un nombre a la estructura anónima. El comportamiento en tiempo de ejecución de las estructuras no anónima es el mismo, independientemente de la versión del compilador.  
  
    ```  
    #include <stdio.h> struct S { S() { printf("Creating S.\n"); } ~S() { printf("Destroying S\n"); } }; union U { struct { S s; } namedStruct; U() {} ~U() {} }; void f() { U u; } int main() { f(); char s[1024]; printf("Press any key.\n"); gets_s(s); return 0; }  
    ```  
  
     Por otro lado, intente mover el código del constructor y el destructor a funciones nuevas y agregue llamadas a estas funciones desde el constructor y el destructor de la unión.  
  
    ```  
    #include <stdio.h> struct S { void Create() { printf("Creating S.\n"); } void Destroy() { printf("Destroying S\n"); } }; union U { struct { S s; }; U() { s.Create();  } ~U() { s.Destroy(); } }; void f() { U u; } int main() { f(); char s[1024]; printf("Press any key.\n"); gets_s(s); return 0; }  
    ```  
  
-   **Resolución de plantilla**  
  
     Se han hecho cambios en la resolución de nombres de plantillas. En C\+\+, al pensar en candidatos para la resolución de un nombre, puede darse el caso de que uno o más de los nombres considerados como coincidencias posibles produzcan una creación de instancias de plantilla no válida. Normalmente, estas instancias no válidas no provocan errores del compilador; este principio se conoce como SFINAE \(Substitution Failure Is Not An Error\).  
  
     Ahora, si SFINAE requiere que el compilador cree una instancia de la especialización de una plantilla de clase, los errores que se producen durante este proceso son errores del compilador. En versiones anteriores, el compilador omitiría esos errores. Por ejemplo, considere el siguiente código:  
  
    ```  
    #include <type_traits> template<typename T> struct S { S() = default; S(const S&); S(S&&); template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type> S(S<U>&&); }; struct D; void f1() { S<D> s1; S<D> s2(s1); } struct B { }; struct D : public B { }; void f2() { S<D> s1; S<D> s2(s1); }  
  
    ```  
  
     Si usa el compilador actual, obtendrá el siguiente error:  
  
    ```Output  
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of' ..\t331.cpp(14): note: see declaration of 'D' ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled with [ T=D, U=D ]  
    ```  
  
     Esto se debe a que el punto de la primera invocación de is\_base\_of de la clase 'D' aún no se ha definido.  
  
     En este caso, la solución es no usar los rasgos de tipos \(type traits\) mientras no se defina la clase. Si mueve las definiciones de B y D al principio del archivo de código, el error se soluciona. Si las definiciones están en archivos de encabezado, compruebe el orden de las instrucciones include para los archivos de encabezado a fin de asegurarse de que las definiciones de clase se compilan antes de que se usen las plantillas problemáticas.  
  
-   **Constructores de copias**  
  
     Tanto en [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] como en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)], el compilador genera un constructor de copias para una clase si esa clase tiene un constructor de movimiento definido por el usuario, pero ningún constructor de copias definido por el usuario. En Dev14, este constructor de copias generado implícitamente también se marca como "\= delete".  
  
##  <a name="BK_CRT"></a> Biblioteca en tiempo de ejecución de C \(CRT\)  
  
### Cambios generales  
  
-   **Binarios refactorizados**  
  
     La biblioteca CRT se ha refactorizado en dos binarios distintos: un CRT universal \(ucrtbase\), que contiene la mayor parte de la funcionalidad estándar, y una biblioteca de VC Runtime \(vcruntime140\), que contiene la funcionalidad relacionada con el compilador como el control de excepciones y funciones intrínsecas. Si usa la configuración predeterminada del proyecto, entonces este cambio no le afecta ya que el vinculador usará automáticamente las nuevas bibliotecas predeterminadas. Si ha configurado la propiedad del **Vinculador** del proyecto **Omitir todas las bibliotecas predeterminadas** en **Sí** o si usa la opción del vinculador \/NODEFAULTLIB en la línea de comandos, debe actualizar la lista de bibliotecas \(en la propiedad **Dependencias adicionales**\) para incluir las nuevas bibliotecas refactorizadas. Reemplace la biblioteca CRT anterior \(libcmt.lib, libcmtd.lib, msvcrt.lib, msvcrtd.lib\) por las bibliotecas refactorizadas equivalentes. Para cada una de las dos bibliotecas refactorizadas hay versiones estáticas \(.lib\) y versiones dinámicas \(.dll\), así como versiones de lanzamiento \(sin sufijo\) y versiones de depuración \(con el sufijo “d”\). Las versiones dinámicas tienen una biblioteca de importación con la que se establece el vínculo. Las dos bibliotecas refactorizadas son CRT universal, concretamente ucrtbase.dll o .lib, ucrtbased.dll o .lib y la biblioteca de VC Runtime, libvcruntime.lib, libvcruntime.dll, libvcruntimed.lib y libvcruntimed.dll. Vea [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md).  
  
### \<locale.h\>  
  
-   **localeconv**  
  
     La función [localeconv](../c-runtime-library/reference/localeconv.md) declarada en locale.h ahora funciona correctamente cuando la [configuración regional por subproceso](../parallel/multithreading-and-locales.md) está habilitada. En versiones anteriores de la biblioteca, esta función devolvía los datos de lconv de la configuración regional global, no de la configuración regional del subproceso.  
  
     Si usa la configuración regional por subproceso, compruebe la utilización de localeconv para ver si el código asume que los datos de lconv devueltos corresponden a la configuración regional global y modifíquelo debidamente.  
  
### \<math.h\>  
  
-   **Sobrecargas de C\+\+ de funciones de la biblioteca matemática**  
  
     En versiones anteriores, \<math.h\> definía algunas de las sobrecargas de C\+\+ para las funciones de la biblioteca matemática, pero no todas. \<cmath\> definía las sobrecargas restantes por lo que, para obtener todas las sobrecargas, era necesario incluir el encabezado \<cmath\>. Esto causaba problemas con la resolución de sobrecargas de función en el código que solo incluía \<math.h\>. Ahora, todas las sobrecargas de C\+\+ se han quitado de \<math.h\> y solo están presentes en \<cmath\>.  
  
     Para resolver errores, incluya \<cmath\> para obtener las declaraciones de las funciones que se quitaron de \<math.h\>. En la tabla siguiente se muestran las funciones que se han movido.  
  
     Funciones movidas:  
  
    1.  double abs\(double\) y float abs\(float\)  
  
    2.  double pow\(double, int\), float pow\(float, float\), float pow\(float, int\), long double pow\(long double, long double\), long double pow\(long double, int\)  
  
    3.  float y versiones long double de funciones de punto flotante acos, acosh, asin, asinh, atan, atanh, atan2, cbrt, ceil, copysign, cos, cosh, erf, erfc, exp, exp2, expm1, fabs, fdim, floor, fma, fmax, fmin, fmod, frexp, hypot, ilogb, ldexp, lgamma, llrint, llround, log, log10, log1p, log2, lrint, lround, modf, nearbyint, nextafter, nexttoward, remainder, remquo, rint, round, scalbln, scalbn, sin, sinh, sqrt, tan, tanh, tgamma, trunc  
  
     Si tiene código que use abs con un tipo de punto flotante que solo incluya el encabezado math.h, las versiones de punto flotante ya no estarán disponibles, por lo que la llamada, incluso con un argumento de punto flotante, se resuelve ahora como abs\(int\). Esto produce el error:  
  
    ```Output  
    advertencia C4244: 'argument': conversión de 'float' a 'int'; posible pérdida de datos  
    ```  
  
     La solución para esta advertencia es reemplazar la llamada a abs por una versión de punto flotante de abs, como fabs para un argumento de tipo double o fabsf para un argumento de tipo float, o incluir el encabezado cmath y seguir usando abs.  
  
-   **Conformidad de punto flotante**  
  
     Se han introducido muchos cambios en la biblioteca matemática para mejorar la conformidad con las especificaciones IEEE\-754 y el anexo F de C11 con respecto a entradas de casos especiales como infinitos y valores NaN. Por ejemplo, las entradas de valores NaN simples, que a menudo se trataban como errores en las versiones anteriores de la biblioteca, ya no se consideran como tales. Consulte el [estándar IEEE 754](http://grouper.ieee.org/groups/754) y el anexo F del [estándar C11](http://www.iso-9899.info/wiki/The_Standard).  
  
     Estos cambios no provocarán errores en tiempo de compilación, pero pueden hacer que los programas se comporten de manera diferente y más correcta según el estándar.  
  
-   **FLT\_ROUNDS**  
  
     En Visual Studio 2013, la macro FLT\_ROUNDS se expandía a una expresión constante, lo cual era incorrecto porque el modo de redondeo es configurable en tiempo de ejecución, por ejemplo, al llamar a fesetround. La macro FLT\_ROUNDS ahora es dinámica y refleja correctamente el modo de redondeo actual.  
  
### \<new\> y \<new.h\>  
  
-   **new y delete**  
  
     En versiones anteriores de la biblioteca, las funciones new y delete del operador definido por la implementación se exportaban desde la DLL de la biblioteca en tiempo de ejecución \(por ejemplo, msvcr120.dll\). Ahora, estas funciones de operador siempre se vinculan estáticamente en los archivos binarios, incluso cuando se usan las DLL de la biblioteca en tiempo de ejecución.  
  
     Esto no supone una novedad para el código nativo o mixto \(\/clr\); no obstante, para el código compilado como [\/clr:pure](../build/reference/clr-common-language-runtime-compilation.md), puede provocar que el código no se compile. Si compila código como \/clr:pure, quizá deba agregar \#include \<new\> o \#include \<new.h\> para evitar los errores de compilación debidos a este cambio. Tenga en cuenta que \/clr:pure ha quedado en desuso en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] y es posible que se desaparezca en futuras versiones.  
  
### \<process.h\>  
  
-   **\_beginthread y \_beginthreadex**  
  
     Las funciones [\_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) y [\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) ahora contienen una referencia al módulo donde se define el procedimiento de subproceso para la duración del subproceso. Esto ayuda a garantizar que los módulos no se descargan hasta que un subproceso se ejecuta hasta su finalización.  
  
### \<stdarg.h\>  
  
-   **va\_start y tipos de referencia**  
  
     Cuando se compila código C\+\+, [va\_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) ahora valida en tiempo de compilación que el argumento que se le pasa no es de tipo de referencia. Los argumentos de tipo de referencia están prohibidos por el estándar de C\+\+.  
  
### \<stdio.h\> y \<conio.h\>  
  
-   **La familia de funciones printf y scanf se define ahora en línea.**  
  
     Las definiciones de todas las funciones printf y scanf se han movido en línea en \<stdio.h\>, \<conio.h\> y otros encabezados de CRT. Se trata de una novedad importante que lleva a un error del vinculador \(LNK2019, símbolo externo sin resolver\) en todos los programas que declaran localmente estas funciones sin incluir los encabezados de CRT apropiados. Si es posible, actualice el código para incluir los encabezados de CRT \(es decir, agregue \#include \<stdio.h\>\) y las funciones en línea. Si prefiere no modificar el código para incluir estos archivos de encabezado, una solución alternativa es agregar una biblioteca adicional a su entrada de vinculador, legacy\_stdio\_definitions.lib.  
  
     Para agregar esta biblioteca a la entrada de vinculador en el IDE, abra el menú contextual del nodo de proyecto y elija **Propiedades**. A continuación, en el cuadro de diálogo **Propiedades del proyecto**, seleccione **Vinculador**, y edite **Entrada del vinculador** para agregar legacy\_stdio\_definitions.lib a la lista separada por signos de punto y coma.  
  
     Si el proyecto está vinculado a las bibliotecas estáticas que se compilaron con una versión de Visual C\+\+ anterior a 2015, el vinculador podría informar de un símbolo externo sin resolver. Estos errores pueden hacer referencia a las definiciones de stdio internas de for \_iob, \_iob\_func, o a importaciones relacionadas para determinadas funciones stdio en formato \_imp\_\*. Microsoft le recomienda que, cuando actualice un proyecto, recompile todas las bibliotecas estáticas con la versión más reciente del compilador y las bibliotecas de C\+\+. Si la biblioteca es una biblioteca de terceros para la que el origen no está disponible, solicite al autor un binario actualizado o encapsule su uso de la biblioteca en un archivo DLL independiente que luego compile con la versión anterior del compilador y las bibliotecas de Visual C\+\+.  
  
    > [!WARNING]
    >  Si se vincula con el SDK de Windows 8.1 o con versiones anteriores, es posible encontrar estos errores de símbolo externo sin resolver. En ese caso, debe resolver el error agregando legacy\_stdio\_definitions.lib a la entrada de vinculador tal como se describió anteriormente.  
  
     Para solucionar errores de símbolo sin resolver, puede probar a usar [dumpbin.exe](../build/reference/dumpbin-reference.md) para examinar los símbolos definidos en un archivo binario. Pruebe la siguiente línea de comandos para ver los símbolos definidos en una biblioteca.  
  
    ```  
    dumpbin.exe /LINKERMEMBER somelibrary.lib  
    ```  
  
-   **gets y \_getws**  
  
     Las funciones [gets](../c-runtime-library/gets-getws.md) y [\_getws](../c-runtime-library/gets-getws.md) se han quitado. La función gets se quitó de la biblioteca estándar de C en C11 porque su uso no es seguro. La función \_getws era una extensión de Microsoft que equivalía a gets, pero para cadenas de caracteres anchos. Como alternativa a estas funciones, puede usar [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [gets\_s](../c-runtime-library/reference/gets-s-getws-s.md) y [\_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md).  
  
-   **\_cgets y \_cgetws**  
  
     Las funciones [\_cgets](../c-runtime-library/cgets-cgetws.md) y [\_cgetws](../c-runtime-library/cgets-cgetws.md) se han quitado. Como alternativa a estas funciones, puede usar [\_cgets\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) y [\_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
-   **Formato de Infinity y NaN**  
  
     En versiones anteriores, los valores infinitos y NaN adoptaban el formato mediante un conjunto de cadenas centinela específicas de Visual C\+\+.  
  
    -   Infinito: 1.\#INF  
  
    -   NaN simple: 1. \#QNAN  
  
    -   NaN de señalización: 1.\#SNAN  
  
    -   NaN indefinido: 1.\#IND  
  
     Cualquiera de estas cadenas podía prefijarse con un signo y tener un formato ligeramente diferente según el ancho de campo y la precisión \(a veces con efectos inusuales, p. ej., printf\("%.2f\\n", INFINITY\) imprimía 1.\#J porque \#INF se "redondeaba" a una precisión de dos dígitos\). C99 introdujo nuevos requisitos en el formato de los valores infinitos y NaN. La implementación de Visual C\+\+ ahora cumple estos requisitos. Las nuevas cadenas son las siguientes:  
  
    -   Infinito: inf  
  
    -   NaN simple: nan  
  
    -   NaN de señalización: nan\(snan\)  
  
    -   NaN indefinido: nan\(ind\)  
  
     Cualquiera de ellas puede ir precedida por un signo. Si se usa un especificador de formato en mayúscula \(%F en lugar de %f\), las cadenas se imprimen en mayúscula \(INF en lugar de inf\), según sea necesario.  
  
     Las funciones [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) se han modificado para analizar estas nuevas cadenas de manera que harán un recorrido de ida y vuelta a través de printf y scanf.  
  
-   **Formato y análisis de punto flotante**  
  
     Se han introducido nuevos algoritmos de análisis y formato de punto flotante para mejorar la corrección. Este cambio afecta a las familias de funciones [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) y [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), además de a otras funciones como [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).  
  
     Los algoritmos de formato anteriores generaban únicamente un número limitado de dígitos y rellenaban con cero el resto de posiciones decimales. Esto suele bastar para generar cadenas que hagan un recorrido de ida y vuelta hasta al valor de punto flotante original, pero no si se desea que el valor sea exacto \(o la representación decimal más cercana al mismo\). Los nuevos algoritmos de formato generan tantos dígitos como sea necesario para representar el valor \(o para rellenar la precisión especificada\). Como ejemplo de la mejora, considere los resultados cuando se imprime una gran potencia de dos:  
  
    ```  
    printf("%.0f\n", pow(2.0, 80))  
  
    ```  
  
    ```Output  
        Old: 1208925819614629200000000    New: 1208925819614629174706176  
    ```  
  
     Los algoritmos de análisis antiguos solo tenían en cuenta un máximo de 17 dígitos significativos de la cadena de entrada y descartaban el resto de los dígitos. Esto es suficiente para generar una aproximación muy precisa del valor representado por la cadena y el resultado suele acercarse mucho al resultado redondeado correctamente. La nueva implementación tiene en cuenta todos los dígitos presentes y genera el resultado redondeado correctamente para todas las entradas \(hasta 768 dígitos de longitud\). Además, estas funciones ahora respetan el modo de redondeo \(que se puede controlar a través de fesetround\).  Este es un cambio de comportamiento potencialmente importante porque estas funciones pueden generar resultados diferentes. Los nuevos resultados siempre son más correctos que los resultados anteriores.  
  
-   **Análisis de punto flotante de hexadecimal e infinity\/NaN**  
  
     Los algoritmos de análisis de punto flotante ahora analizan cadenas hexadecimales de punto flotante \(como las generadas por los especificadores de formato de printf %a y %A\) y todas las cadenas infinity y NaN generadas por las funciones de printf, como se describió anteriormente.  
  
-   **Relleno de ceros a la izquierda de %A y %a**  
  
     Los especificadores de formato %a y %A dan formato a un número de punto flotante como mantisa hexadecimal y exponente binario. En versiones anteriores, las funciones de printf rellenaban con ceros las cadenas de manera incorrecta. Por ejemplo, printf\("%07.0a\\n", 1.0\) imprimía 00x1p\+0, cuando debería imprimir 0x01p\+0. Esto se ha solucionado.  
  
-   **Precisión de %A y %a**  
  
     La precisión predeterminada de los especificadores de formato %A y %a era de 6 en versiones anteriores de la biblioteca. La precisión predeterminada es ahora de 13, de conformidad con el estándar de C.  
  
     Se trata de un cambio de comportamiento en tiempo de ejecución en la salida de cualquier función que usa una cadena de formato con %A o %a. En el comportamiento anterior, la salida que usaba el especificador %A podía ser “1.1A2B3Cp\+111”. Ahora, la salida para el mismo valor es “1.1A2B3C4D5E6F7p\+111”. Para obtener el comportamiento anterior, puede especificar la precisión, por ejemplo, %.6A. Vea [Especificación de precisión](../c-runtime-library/precision-specification.md).  
  
-   **Especificador %F**  
  
     Ahora se admite el especificador de formato\/conversión %F. Es funcionalmente equivalente al especificador de formato %f, salvo que el formato de los valores infinitos y NaN es con letras mayúsculas.  
  
     En versiones anteriores, la implementación solía analizar F y N como modificadores de longitud. Este comportamiento se remontaba a la época de los espacios de direcciones segmentados: estos modificadores de longitud se usaban para indicar punteros far y near, respectivamente, como en %Fp o %Ns. Este comportamiento se ha eliminado. Si se encuentra %F, ahora se trata como el especificador de formato %F; si se encuentra %N, ahora se trata como un parámetro no válido.  
  
-   **Formato de exponente**  
  
     Los especificadores de formato %e y %E dan formato a un número de punto flotante como mantisa decimal y exponente. En algunos casos, los especificadores de formato %g y %G también dan este formato a los números. En versiones anteriores, CRT generaba siempre las cadenas con exponentes de tres dígitos. Por ejemplo, printf\("%e\\n", 1.0\) imprimía 1.000000e\+000. Ese comportamiento era incorrecto: C exige que si el exponente solo se puede representar mediante uno o dos dígitos, entonces solo se imprimirán dos dígitos.  
  
     En Visual Studio 2005 se agregó un modificador de conformidad global: [\_set\_output\_format](../c-runtime-library/set-output-format.md). Un programa podía llamar a esta función con el argumento \_TWO\_DIGIT\_EXPONENT, para habilitar la impresión de exponentes conforme a los estándares. El comportamiento predeterminado se ha cambiado al modo de impresión de exponentes conforme a los estándares.  
  
-   **Validación de cadenas de formato**  
  
     En versiones anteriores, las funciones printf y scanf aceptaban en modo silencioso muchas cadenas de formato no válido, a veces con efectos inesperados. Por ejemplo, %hlhlhld se trataba como %d. Ahora, todas las cadenas de formato no válido se tratan como parámetros no válidos.  
  
-   **validación de cadenas de modo fopen**  
  
     En versiones anteriores, la familia de funciones fopen aceptaba en modo silencioso algunas cadenas de modo no válido \(por ejemplo, r\+b\+\). Ahora, las cadenas de modo no válido se consideran como parámetros no válidos.  
  
-   **Modo \_O\_U8TEXT**  
  
     La función [\_setmode](../c-runtime-library/reference/setmode.md) ahora informa correctamente del modo de flujos abiertos en modo \_O\_U8TEXT. En versiones anteriores de la biblioteca, informaba de que dichos flujos se abrían en \_O\_WTEXT.  
  
     Se trata de una novedad importante si su código interpreta el modo \_O\_WTEXT para los flujos en que la codificación es UTF\-8. Si su aplicación no es compatible con UTF\_8, considere la posibilidad de agregar compatibilidad con esta codificación cada vez más común.  
  
-   **snprintf y vsnprintf**  
  
     Las funciones [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) y [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) están ahora implementadas. A menudo, el código anterior proporcionaba versiones de macro de definiciones de estas funciones porque la biblioteca CRT no las implementaba, pero ya no son necesarias en las versiones más recientes. Si [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) o [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) se definen como una macro antes de incluir \<stdio.h\>, la compilación produce un error que indica donde estaba definida la macro.  
  
     Normalmente, la solución a este problema consiste en eliminar todas las declaraciones de snprintf o vsnprintf en el código de usuario.  
  
-   **tmpnam genera nombres de archivo utilizables**  
  
     En versiones anteriores, las funciones tmpnam y tmpnam\_s generaban nombres de archivo en la raíz de la unidad \(por ejemplo, \\sd3c.\). Estas funciones generan ahora rutas de nombre de archivo utilizables en un directorio temporal.  
  
-   **Encapsulación FILE**  
  
     En versiones anteriores, FILE estaba totalmente definido en \<stdio.h\>, por lo que el código de usuario podía obtener acceso a FILE y modificar sus elementos internos. La biblioteca stdio se ha cambiado para ocultar los detalles de implementación. Como parte de esto, FILE, tal como se define en \<stdio.h\> es ahora un tipo opaco y sus miembros son inaccesibles desde fuera de la propia biblioteca CRT.  
  
-   **\_outp y \_inp**  
  
     Las funciones [\_outp](../c-runtime-library/outp-outpw-outpd.md), [\_outpw](../c-runtime-library/outp-outpw-outpd.md), [\_outpd](../c-runtime-library/outp-outpw-outpd.md), [\_inp](../c-runtime-library/inp-inpw-inpd.md), [\_inpw](../c-runtime-library/inp-inpw-inpd.md) y [\_inpd](../c-runtime-library/inp-inpw-inpd.md) se han quitado.  
  
### \<stdlib.h\>, \<malloc.h\> y \<sys\/stat.h\>  
  
-   **strtof y wcstof**  
  
     Las funciones strtof y wcstof no podían establecer errno en ERANGE si el valor no era representable como un float. Esto se ha solucionado. \(Observe que este error era específico de estas dos funciones; las funciones strtod, wcstod, strtold y wcstold no se veían afectadas\). Se trata de una novedad importante en tiempo de ejecución.  
  
-   **Funciones de asignación alineadas**  
  
     En versiones anteriores, las funciones de asignación alineadas \(\_aligned\_malloc, \_aligned\_offset\_malloc, etc.\) aceptaban en modo silencioso las solicitudes para un bloque de alineación de 0. La alineación solicitada debe ser una potencia de dos, y cero no lo es. Esto se ha corregido. Ahora, una alineación solicitada de 0 se trata como un parámetro no válido. Se trata de una novedad importante en tiempo de ejecución.  
  
-   **Funciones de montón**  
  
     Las funciones \_heapadd, \_heapset y \_heapused se han quitado. Estas funciones dejaron de ser funcionales cuando el CRT se actualizó para usar el montón de Windows.  
  
-   **smallheap**  
  
     La opción de vínculo smallheap se ha quitado. Vea [Opciones de vínculo](../c-runtime-library/link-options.md).  
  
### \<string.h\>  
  
-   **wcstok**  
  
     La firma de la función wcstok se cambió para que coincida con los requisitos del estándar de C. En versiones anteriores de la biblioteca, la firma de esta función era:  
  
    ```  
    wchar_t* wcstok(wchar_t*, wchar_t const*)  
    ```  
  
     Usaba un contexto interno por subproceso para realizar un seguimiento del estado a través de las llamadas, como se hace para strtok. La función ahora tiene la firma wchar\_t\* wcstok\(wchar\_t\*, wchar\_t const\*, wchar\_t\*\*\) y requiere que el llamador pase el contexto como un tercer argumento a la función.  
  
     Se ha agregado una nueva función \_wcstok con la firma anterior para facilitar la portabilidad. Al compilar código de C\+\+, también hay una sobrecarga en línea del wcstok que tiene la firma anterior. Esta sobrecarga se declara en desuso. En el código de C, puede definir \_CRT\_NON\_CONFORMING\_WCSTOK para que \_wcstok se use en lugar de wcstok.  
  
### \<time.h\>  
  
-   **clock**  
  
     En versiones anteriores, la función [clock](../c-runtime-library/reference/clock.md) se implementa mediante la API de Windows [GetSystemTimeAsFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724397.aspx). Con esta implementación, la función clock era sensible a la hora del sistema y no era necesariamente monotónica. La función clock se ha implementado de nuevo en términos de [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) y ahora es monotónica.  
  
-   **fstat y \_utime**  
  
     En versiones anteriores, las funciones [\_stat](../c-runtime-library/reference/stat-functions.md), [fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) y [\_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) controlaban el horario de verano de manera incorrecta. Antes de Visual Studio 2013, todas estas funciones ajustaban incorrectamente las horas del horario estándar como si estuvieran en el horario de verano.  
  
     En Visual Studio 2013, el problema se solucionó en la familia de funciones \_stat, pero no se corrigieron los problemas similares en las familias de funciones fstat y \_utime. Esto provoca problemas debido a la incoherencia entre las funciones. Las familias de funciones fstat y \_utime ya se han corregido, por lo que todas estas funciones controlan ahora el horario de verano de manera correcta y coherente.  
  
-   **asctime**  
  
     En versiones anteriores, la función [asctime](../c-runtime-library/reference/asctime-wasctime.md) rellenaba los días de un dígito con un cero inicial, por ejemplo: Vie Jun 06 08:00:00 2014. La especificación requiere que estos días se rellenen con un espacio inicial, por ejemplo: vie jun  6 08:00:00 2014. Esto se ha solucionado.  
  
-   **strftime y wcsftime**  
  
     Ahora, las funciones strftime y wcsftime admiten los especificadores de formato %C, %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u y %V. Además, los modificadores E y O se analizan, pero se ignoran.  
  
     El especificador de formato %c se especifica como la producción de una “representación de fecha y hora adecuada” para la configuración regional actual. En la configuración regional de C, esta representación debe ser la misma que %a %b %e %T %Y. Se trata de la misma forma producida por asctime. En versiones anteriores, el especificador de formato %c representaba incorrectamente las horas con un formato MM\/DD\/YY HH:MM:SS. Esto se ha solucionado.  
  
-   **timespec y TIME\_UTC**  
  
     Ahora, el encabezado \<time.h\> define el tipo de timespec y la función timespec\_get a partir del estándar de C11. Además, ahora está definida la macro TIME\_UTC para su uso con la función timespec\_get. Se trata de una novedad importante para el código que tiene una definición que está en conflicto con alguna de estas funciones.  
  
-   **CLOCKS\_PER\_SEC**  
  
     La macro CLOCKS\_PER\_SEC ahora se expande a un entero de tipo clock\_t, tal como exige el lenguaje C.  
  
###  <a name="BK_STL"></a> Biblioteca de plantillas estándar  
 Para habilitar nuevas optimizaciones y comprobaciones de depuración, la implementación de Visual Studio de la Biblioteca estándar de C\+\+ interrumpe deliberadamente la compatibilidad binaria de una versión a la siguiente. Por consiguiente, cuando se utiliza la Biblioteca estándar de C\+\+, los archivos de objetos y las bibliotecas estáticas que se han compilado con versiones diferentes no se pueden combinar en un binario \(EXE o DLL\), y los objetos de la Biblioteca estándar de C\+\+ no se pueden pasar entre los archivos binarios que se han compilado con versiones diferentes. Una combinación de este estilo emite errores del vinculador sobre discordancias \_MSC\_VER. \(\_MSC\_VER es la macro que contiene la versión principal del compilador, por ejemplo, 1800 para Visual Studio 2013\). Esta comprobación no detecta la combinación de archivos DLL ni detecta combinaciones que impliquen Visual C\+\+ 2008 o versiones anteriores.  
  
-   **Archivos de inclusión de STL**  
  
     Algunos cambios se realizaron en la estructura include en los encabezados STL. Los encabezados de STL pueden incluirse entre sí de maneras no especificadas. En general, debe escribir el código para que incluya todos los encabezados necesarios según el estándar de C\+\+ y que no se base en las inclusiones mutuas entre encabezados STL. Con esto se logra que el código sea portable entre versiones y plataformas. Al menos dos de los cambios en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] afectan al código de usuario. En primer lugar, \<string\> ya no incluye \<iterator\>. En segundo lugar, ahora \<tuple\> declara std::array sin incluir todas las \<array\>. Esto puede dañar el código a través de la siguiente combinación de construcciones de código: el código tiene una variable denominada “array” y tiene una directiva using “using namespace std;”, y se incluye un encabezado STL \(por ejemplo, \<functional\>\) que incluye \<tuple\>, que ahora declara std::array.  
  
-   **steady\_clock**  
  
     La implementación de \<chrono\> de [steady\_clock](../standard-library/steady-clock-struct.md) ha cambiado para cumplir los requisitos del estándar de C\+\+ en cuanto a estabilidad y monotonía \(steadiness y monotonicity\). steady\_clock ahora se basa en [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx), y high\_resolution\_clock ahora es una typedef para steady\_clock. Como resultado, en Visual C\+\+ steady\_clock::time\_point es ahora un typedef para chrono::time\_point \<steady\_clock\>; sin embargo, esto no es necesariamente así en otras implementaciones.  
  
-   **asignadores y const**  
  
     Ahora es necesario que las comparaciones de igualdad y desigualdad de asignadores acepten argumentos const en ambos lados.  Si sus asignadores definen estos operadores del modo siguiente:  
  
    ```  
    bool operator==(const MyAlloc& other)  
    ```  
  
     Debe actualizar estos elementos para declararlos como miembros const.  
  
    ```  
    bool operator==(const MyAlloc& other) const  
    ```  
  
-   **elementos const**  
  
     El estándar de C\+\+ siempre ha prohibido contenedores de elementos const \(como vector\<const T\> o set\<const T\>\). En Visual C\+\+ 2013 y versiones anteriores sí se aceptaban dichos contenedores. En la versión actual, estos contenedores no se compilan.  
  
-   **std::allocator::deallocate**  
  
     En Visual C\+\+ 2013 y versiones anteriores, std::allocator::deallocate\(p, n\) ignoraba el argumento pasado para n.  El estándar de C\+\+ siempre ha requerido que n sea igual que el valor pasado como primer argumento a la invocación de allocate que devuelve p. Sin embargo, en la versión actual, se inspecciona el valor de n. El código que pasa argumentos para n que difieren de lo que el estándar requiere puede bloquearse en tiempo de ejecución.  
  
-   **hash\_map y hash\_set**  
  
     Los archivos de encabezado no estándar hash\_map y hash\_set han quedado en desuso en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] y se eliminarán en una versión futura. En su lugar, use unordered\_map y unordered\_set.  
  
-   **comparadores y operator\(\)**  
  
     Los contenedores asociativos \(la familia \<map\>\) ahora exigen que sus comparadores tengan operadores de llamada de función invocables por constructores. Este código de declaración de clase de comparador ahora no se puede compilar:  
  
    ```  
    bool operator()(const X& a, const X& b)  
    ```  
  
     Para resolver este error, cambie la declaración de función a:  
  
    ```  
    bool operator()(const X& a, const X& b) const  
    ```  
  
-   **rasgos de tipos**  
  
     Se han quitado los nombres anteriores de rasgos de tipos \(type traits\) de una versión anterior del proyecto de estándar de C\+\+. Se cambiaron en C\+\+11 y se han actualizado a los valores de C\+\+11 en [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)]. En la tabla siguiente se muestran los nombres anteriores y los nuevos.  
  
    |Nombre anterior|Nuevo nombre|  
    |---------------------|------------------|  
    |add\_reference|add\_lvalue\_reference|  
    |has\_default\_constructor|is\_default\_constructible|  
    |has\_copy\_constructor|is\_copy\_constructible|  
    |has\_move\_constructor|is\_move\_constructible|  
    |has\_nothrow\_constructor|is\_nothrow\_default\_constructible|  
    |has\_nothrow\_default\_constructor|is\_nothrow\_default\_constructible|  
    |has\_nothrow\_copy|is\_nothrow\_copy\_constructible|  
    |has\_nothrow\_copy\_constructor|is\_nothrow\_copy\_constructible|  
    |has\_nothrow\_move\_constructor|is\_nothrow\_move\_constructible|  
    |has\_nothrow\_assign|is\_nothrow\_copy\_assignable|  
    |has\_nothrow\_copy\_assign|is\_nothrow\_copy\_assignable|  
    |has\_nothrow\_move\_assign|is\_nothrow\_move\_assignable|  
    |has\_trivial\_constructor|is\_trivially\_default\_constructible|  
    |has\_trivial\_default\_constructor|is\_trivially\_default\_constructible|  
    |has\_trivial\_copy|is\_trivially\_copy\_constructible|  
    |has\_trivial\_move\_constructor|is\_trivially\_move\_constructible|  
    |has\_trivial\_assign|is\_trivially\_copy\_assignable|  
    |has\_trivial\_move\_assign|is\_trivially\_move\_assignable|  
    |has\_trivial\_destructor|is\_trivially\_destructible|  
  
-   **Directivas launch::any y launch::sync**  
  
     Las directivas no estándar launch::any y launch::sync se han quitado. En su lugar, para launch::any, use launch:async &#124; launch:deferred. Para launch::sync, use launch::deferred. Vea [launch \(Enumeración\)](../Topic/launch%20Enumeration.md).  
  
###  <a name="BK_MFC"></a> MFC y ATL  
  
-   Debido a su gran tamaño, **Microsoft Foundation Classes \(MFC\)** ya no se incluye en la instalación “típica” de Visual Studio. Para instalar MFC, elija la opción de instalación personalizada en el programa de instalación de Visual Studio 2015. Si ya tiene instalado Visual Studio 2015 y desea instalar MFC, vuelva a ejecutar el programa de instalación de Visual Studio, elija la opción de instalación personalizada y elija Microsoft Foundation Classes. Puede volver a ejecutar el programa de instalación de Visual Studio desde el Panel de control, Programas y características, o desde el medio de instalación.  
  
     El paquete redistribuible de Visual C\+\+ todavía incluye esta biblioteca.  
  
###  <a name="BK_ConcRT"></a> Runtime de simultaneidad  
  
-   **Macro Yield de Windows.h en conflicto con concurrency::Context::Yield**  
  
     El Runtime de simultaneidad usaba anteriormente \#undef para anular las definiciones de la macro Yield a fin de evitar conflictos entre la macro Yield definida en Windows.h h y la función concurrency::Context::Yield. Se ha quitado \#undef y se ha agregado una nueva llamada de API equivalente que no crea un conflicto: [concurrency::Context::YieldExecution](../Topic/Context::YieldExecution%20Method.md). Para evitar conflictos con Yield, puede actualizar el código para llamar a la función YieldExecution o incluya el nombre de la función Yield entre paréntesis en los sitios de llamada, como en el ejemplo siguiente:  
  
    ```  
    (concurrency::Context::Yield)();  
    ```  
  
## Vea también  
 [Introducción](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md)   
 [Cambios importantes en Visual C\+\+ 2013](https://msdn.microsoft.com/library/hh409293.aspx)