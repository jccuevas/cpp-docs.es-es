---
title: Bienvenido a C++ (C++ moderno) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63e73657c7e018d2a4eb71170561e310aeba9d5b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32424872"
---
# <a name="welcome-back-to-c-modern-c"></a>Aquí está otra vez C++ (C++ moderno)
C++ es uno de los lenguajes de programación más utilizados en el mundo. Los programas bien escritos de C++ son rápidos y eficaces. El lenguaje es más flexible que otros lenguajes, ya que se puede utilizar para crear una amplia gama de aplicaciones, desde divertidos y emocionantes juegos, para software científico de alto rendimiento, hasta controladores de dispositivos, programas incrustados y aplicaciones cliente de Windows. Durante más de 20 años, C++ se ha utilizado para resolver problemas como estos y muchos otros. Lo que es posible que no sepa es que un creciente número de programadores de C++ han doblado la programación estilo C poco elegante de ayer y han puesto C++ moderno en su lugar.  
  
 Uno de los requisitos originales para C++ era la compatibilidad con el lenguaje C. Desde entonces, C++ se ha desarrollado con varias iteraciones, C con clases, la especificación del lenguaje original de C++ y luego las muchas mejoras subsiguientes. Debido a esta herencia, C++ se conoce a menudo como lenguaje de programación multiparadigma. En C++, puede realizar programación puramente de procedimiento de estilo C con punteros sin formato, matrices, cadenas de caracteres terminadas en null, estructuras de datos personalizadas y otras características que pueden ofrecer un gran rendimiento, pero también generar errores y complejidad.  Debido a que la programación de estilo C está llena de peligros como estos, uno de los objetivos fundamentales de C++ era que los programas tuvieran seguridad de tipos y fueran más fáciles de escribir, ampliar y mantener. Desde el principio, C++ adoptó paradigmas de programación tales como la programación orientada a objetos. A lo largo de los años, se han agregado características al lenguaje, junto con bibliotecas estándar altamente probadas de estructuras de datos y algoritmos. Estas adiciones son las que han hecho posible el estilo moderno de C++.  
  
 En el moderno C++ se destaca lo siguiente:  
  
-   Ámbito basado en pila en lugar de ámbito de montón o global estático.  
  
-   Inferencia de tipos automática en lugar de nombres de tipo explícitos.  
  
-   Punteros inteligentes en lugar de punteros sin formato.  
  
-   `std::string` y `std::wstring` tipos (vea [ \<cadena >](../standard-library/string.md)) en lugar de sin formato `char[]` matrices.  
  
-   [Biblioteca estándar de C++](../standard-library/cpp-standard-library-header-files.md) como contenedores `vector`, `list`, y `map` en lugar de matrices sin formato o contenedores personalizados. Vea [ \<vector >](../standard-library/vector.md), [ \<lista >](../standard-library/list.md), y [ \<mapa >](../standard-library/map.md).  
  
-   Biblioteca estándar de C++ [algoritmos](../standard-library/algorithm.md) en lugar de forma manual los codificados.  
  
-   Excepciones, para notificar y controlar errores.  
  
-   Sin bloqueo mediante la biblioteca estándar de C++ la comunicación entre subprocesos `std::atomic<>` (consulte [ \<atómica >](../standard-library/atomic.md)) en lugar de otros mecanismos de comunicación entre subprocesos.  
  
-   En línea [funciones lambda](../cpp/lambda-expressions-in-cpp.md) en lugar de pequeñas funciones implementadas por separado.  
  
-   Basado en intervalo for (bucles) escribir bucles más sólidos que funcionan con matrices, los contenedores de la biblioteca estándar de C++ y en tiempo de ejecución de Windows colecciones en el formulario `for ( for-range-declaration : expression )`. Esto forma parte del lenguaje principal. Para obtener más información, consulte [basados en intervalos de instrucción (C++)](../cpp/range-based-for-statement-cpp.md).  
  
 El propio lenguaje C++ también ha evolucionado. Compare los fragmentos de código siguientes. Este muestra cómo eran las cosas en C++:  
  
```cpp  

#include <vector>

void f()
{
    // Assume circle and shape are user-defined types  
    circle* p = new circle( 42 );   
    vector<shape*> v = load_shapes();  

    for( vector<circle*>::iterator i = v.begin(); i != v.end(); ++i ) {  
        if( *i && **i == *p )  
            cout << **i << " is a match\n";  
    }  

    // CAUTION: If v's pointers own the objects, then you
    // must delete them all before v goes out of scope.
    // If v's pointers do not own the objects, and you delete
    // them here, any code that tries to dereference copies
    // of the pointers will cause null pointer exceptions.
    for( vector<circle*>::iterator i = v.begin();  
            i != v.end(); ++i ) {  
        delete *i; // not exception safe  
    }  

    // Don't forget to delete this, too.  
    delete p;  
} // end f()
```

 Aquí se explica cómo se logra lo mismo en C++ moderno:  
  
```cpp

#include <memory>  
#include <vector>  

void f()
{
    // ...  
    auto p = make_shared<circle>( 42 );  
    vector<shared_ptr<shape>> v = load_shapes();  

    for( auto& s : v ) 
    {  
        if( s && *s == *p )
        {
            cout << *s << " is a match\n";
        }
    }
}

```

 En C++ moderno, no tiene que utilizar control de excepciones nuevo/eliminar o explícito porque puede utilizar los punteros inteligentes en su lugar. Cuando se usa el `auto` deducción de tipos y [función lambda](../cpp/lambda-expressions-in-cpp.md), puede escribir código más rápido, endurecer y entender mejor. Y basada en intervalo `for` bucle es más limpio, fáciles de usar y menos propenso a errores imprevistos que un estilo de C `for` bucle. Puede utilizar código reutilizable con las mínimas líneas de código para escribir la aplicación. También puede hacer que ese código sea seguro para excepciones y seguro para memoria, y que no tenga ninguna asignación/desasignación ni códigos de error que tratar.  
  
 C++ moderno incorpora dos clases de polimorfismo: tiempo de compilación, con plantillas y tiempo de ejecución, con herencia y virtualización. Puede mezclar las dos clases de polimorfismo para aumentar el efecto. La plantilla de la biblioteca estándar de C++ `shared_ptr` utiliza métodos virtuales internos para lograr su borrado de tipos aparentemente sin esfuerzo. No obstante, no utilice demasiado la virtualización para el polimorfismo cuando una plantilla sea la mejor opción. Las plantillas pueden ser muy eficaces.  
  
 Si viene a C++ desde otro lenguaje, especialmente desde un lenguaje administrado en el que la mayoría de los tipos sean tipos de referencia y muy pocos sean tipos de valor, debe saber que las clases de C++ son tipos de valor de forma predeterminada. No obstante, puede especificarlos como tipos de referencia para habilitar comportamiento polimórfico que admita la programación orientada a objetos. Una perspectiva útil: los tipos de valor son más de memoria y control de diseño; los tipos de referencia son más de clases base y funciones virtuales para admitir polimorfismo. De forma predeterminada, los tipos de valor se pueden copiar; cada uno tiene un constructor de copias y un operador de asignación de copia. Cuando se especifica un tipo de referencia, se crea la clase que no se puede copiar (se deshabilita el constructor de copias y el operador de asignación) y se utiliza un destructor virtual, que admite el polimorfismo. Los tipos de valor están también relacionados con el contenido que, cuando se copia, proporciona dos valores independientes que se pueden modificar por separado. No obstante, los tipos de referencia están relacionados con la identidad (el tipo de objeto de que se trata) y, por esta razón, a veces se conocen como tipos polimórficos.  
  
 C++ está resurgiendo porque la eficacia vuelve a ser lo más importante. Los lenguajes como Java y C# son buenos cuando la productividad del programador es importante, pero cuando la eficacia y el rendimiento son primordiales aparecen sus limitaciones. Para aumentar la eficacia, especialmente en dispositivos de hardware limitado, no hay nada mejor que el moderno C++.  
  
 No solo el lenguaje es moderno, las herramientas de desarrollo también lo son. [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] hace que todas las partes del ciclo de desarrollo sean robustas y eficaces. Incluye herramientas de ALM (Administración del ciclo de vida de las aplicaciones), mejoras del IDE como IntelliSense, mecanismos de herramientas fáciles de usar como XAML, compilación, depuración y muchas otras herramientas.  
  
 Los artículos de esta parte de la documentación proporcionan instrucciones y procedimientos recomendados para las características más importantes y técnicas de alto nivel para escribir programas modernos de C++.  
  
-   [Sistema de tipos de C++](../cpp/cpp-type-system-modern-cpp.md)  
  
-   [Inicialización uniforme y constructores de delegación](../cpp/uniform-initialization-and-delegating-constructors.md)  
  
-   [Duración de objetos y administración de recursos](../cpp/object-lifetime-and-resource-management-modern-cpp.md)  
  
-   [Recursos propios de los objetos (RAII)](../cpp/objects-own-resources-raii.md)  
  
-   [Punteros inteligentes](../cpp/smart-pointers-modern-cpp.md)  
  
-   [Pimpl para encapsulación en tiempo de compilación](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)  
  
-   [Contenedores](../cpp/containers-modern-cpp.md)  
  
-   [Algoritmos](../cpp/algorithms-modern-cpp.md)  
  
-   [Cadena y E/S formato (C++ moderno)](../cpp/string-and-i-o-formatting-modern-cpp.md)  
  
-   [Controlar errores y excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)  
  
-   [Portabilidad en los límites de ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)  
  
 Para obtener más información, vea el artículo de StackOverflow [qué giros de C++ están en desuso en C ++ 11](http://go.microsoft.com/fwlink/p/?linkid=402836)  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)  
 [Conformidad del lenguaje Visual C++](../visual-cpp-language-conformance.md)  
