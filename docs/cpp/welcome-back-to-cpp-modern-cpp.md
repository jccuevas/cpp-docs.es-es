---
title: "Aqu&#237; est&#225; otra vez C++ (C++ moderno) | Microsoft Docs"
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
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Aqu&#237; est&#225; otra vez C++ (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ es uno de los lenguajes de programación más utilizados en el mundo.  Los programas bien escritos de C\+\+ son rápidos y eficaces.  El lenguaje es más flexible que otros lenguajes, ya que se puede utilizar para crear una amplia gama de aplicaciones, desde divertidos y emocionantes juegos, para software científico de alto rendimiento, hasta controladores de dispositivos, programas incrustados y aplicaciones cliente de Windows.  Durante más de 20 años, C\+\+ se ha utilizado para resolver problemas como estos y muchos otros.  Lo que es posible que no sepa es que un creciente número de programadores de C\+\+ han doblado la programación estilo C poco elegante de ayer y han puesto C\+\+ moderno en su lugar.  
  
 Uno de los requisitos originales para C\+\+ era la compatibilidad con el lenguaje C.  Desde entonces, C\+\+ se ha desarrollado con varias iteraciones, C con clases, la especificación del lenguaje original de C\+\+ y luego las muchas mejoras subsiguientes.  Debido a esta herencia, C\+\+ se conoce a menudo como lenguaje de programación multiparadigma.  En C\+\+, puede realizar programación puramente de procedimiento de estilo C con punteros sin formato, matrices, cadenas de caracteres terminadas en null, estructuras de datos personalizadas y otras características que pueden ofrecer un gran rendimiento, pero también generar errores y complejidad.  Debido a que la programación de estilo C está llena de peligros como estos, uno de los objetivos fundamentales de C\+\+ era que los programas tuvieran seguridad de tipos y fueran más fáciles de escribir, ampliar y mantener.  Desde el principio, C\+\+ adoptó paradigmas de programación tales como la programación orientada a objetos.  A lo largo de los años, se han agregado características al lenguaje, junto con bibliotecas estándar altamente probadas de estructuras de datos y algoritmos.  Estas adiciones son las que han hecho posible el estilo moderno de C\+\+.  
  
 En el moderno C\+\+ se destaca lo siguiente:  
  
-   Ámbito basado en pila en lugar de ámbito de montón o global estático.  
  
-   Inferencia de tipos automática en lugar de nombres de tipo explícitos.  
  
-   Punteros inteligentes en lugar de punteros sin formato.  
  
-   Tipos `std::string` y `std::wstring` \(vea [\<string\>](../standard-library/string.md)\) en lugar de matrices `char[]` sin formato.  
  
-   Contenedores de [Biblioteca de plantillas estándar](../standard-library/cpp-standard-library-header-files.md) \(STL\) como `vector`, `list` y `map`, en lugar de matrices sin formato o contenedores personalizados.  Vea [\<vector\>](../standard-library/vector.md), [\<list\>](../standard-library/list.md) y [\< map \>](../standard-library/map.md).  
  
-   [Algoritmos de STL](../standard-library/algorithm.md) en lugar de los codificados manualmente.  
  
-   Excepciones, para notificar y controlar errores.  
  
-   Comunicación entre subprocesos sin bloqueos mediante STL `std::atomic<>` \(vea [\<atomic\>](../standard-library/atomic.md)\) en lugar de otros mecanismos de comunicación entre subprocesos.  
  
-   [Funciones lambda](../cpp/lambda-expressions-in-cpp.md) alineadas en lugar de pequeñas funciones implementadas por separado.  
  
-   Bucles basados en intervalos para escribir bucles más eficaces que funcionan con matrices, contenedores STL y colecciones de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] con la forma `for ( for-range-declaration : expression )`.  Esto forma parte del lenguaje principal.  Para obtener más información, vea [Instrucción for basada en intervalo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md).  
  
 El propio lenguaje C\+\+ también ha evolucionado.  Compare los fragmentos de código siguientes.  Este muestra cómo eran las cosas en C\+\+:  
  
```cpp  
  
// circle and shape are user-defined types  
circle* p = new circle( 42 );   
vector<shape*> v = load_shapes();  
  
for( vector<circle*>::iterator i = v.begin(); i != v.end(); ++i ) {  
    if( *i && **i == *p )  
        cout << **i << “ is a match\n”;  
}  
  
for( vector<circle*>::iterator i = v.begin();  
        i != v.end(); ++i ) {  
    delete *i; // not exception safe  
}  
  
delete p;  
  
```  
  
 Aquí se explica cómo se logra lo mismo en C\+\+ moderno:  
  
```cpp  
  
#include <memory>  
#include <vector>  
// ...  
// circle and shape are user-defined types  
auto p = make_shared<circle>( 42 );  
vector<shared_ptr<shape>> v = load_shapes();  
  
for_each( begin(v), end(v), [&](const shared_ptr<shape>& s) {  
    if( s && *s == *p )  
        cout << *s << " is a match\n";  
} );  
  
```  
  
 En C\+\+ moderno, no tiene que utilizar control de excepciones nuevo\/eliminar o explícito porque puede utilizar los punteros inteligentes en su lugar.  Al utilizar la deducción de tipos `auto` y la [función lambda](../cpp/lambda-expressions-in-cpp.md), puede escribir, endurecer y entender mejor el código.  Además, `for_each` es más limpio, más fácil de usar y menos propenso a errores imprevistos que un bucle `for`.  Puede utilizar código reutilizable con las mínimas líneas de código para escribir la aplicación.  También puede hacer que ese código sea seguro para excepciones y seguro para memoria, y que no tenga ninguna asignación\/desasignación ni códigos de error que tratar.  
  
 El C\+\+ moderno incorpora dos tipos de polimorfismo: en tiempo de compilación \(con plantillas\) y en tiempo de ejecución \(con herencia y virtualización\).  Puede mezclar las dos clases de polimorfismo para aumentar el efecto.  La plantilla STL `shared_ptr` utiliza métodos virtuales internos para lograr su borrado de tipos aparentemente sin esfuerzo.  No obstante, no utilice demasiado la virtualización para el polimorfismo cuando una plantilla sea la mejor opción.  Las plantillas pueden ser muy eficaces.  
  
 Si viene a C\+\+ desde otro lenguaje, especialmente desde un lenguaje administrado en el que la mayoría de los tipos sean tipos de referencia y muy pocos sean tipos de valor, debe saber que las clases de C\+\+ son tipos de valor de forma predeterminada.  No obstante, puede especificarlos como tipos de referencia para habilitar comportamiento polimórfico que admita la programación orientada a objetos.  Una perspectiva que puede resultarle útil: los tipos de valor tienen que ver, sobre todo, con el control del diseño y la memoria, mientras que los tipos de referencia tienen más relación con las clases base y las funciones virtuales para admitir el polimorfismo.  De forma predeterminada, los tipos de valor se pueden copiar; cada uno tiene un constructor de copias y un operador de asignación de copia.  Cuando se especifica un tipo de referencia, se crea la clase que no se puede copiar \(se deshabilita el constructor de copias y el operador de asignación\) y se utiliza un destructor virtual, que admite el polimorfismo.  Los tipos de valor están también relacionados con el contenido que, cuando se copia, proporciona dos valores independientes que se pueden modificar por separado.  No obstante, los tipos de referencia están relacionados con la identidad \(el tipo de objeto de que se trata\) y, por esta razón, a veces se conocen como tipos polimórficos.  
  
 C\+\+ está resurgiendo porque la eficacia vuelve a ser lo más importante.  Los lenguajes como Java y C\# son buenos cuando la productividad del programador es importante, pero cuando la eficacia y el rendimiento son primordiales aparecen sus limitaciones.  Para aumentar la eficacia, especialmente en dispositivos de hardware limitado, no hay nada mejor que el moderno C\+\+.  
  
 No solo el lenguaje es moderno, las herramientas de desarrollo también lo son.  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] hace que todas las partes del ciclo de desarrollo sean robustas y eficaces.  Incluye herramientas de ALM \(Administración del ciclo de vida de las aplicaciones\), mejoras del IDE como IntelliSense, mecanismos de herramientas fáciles de usar como XAML, compilación, depuración y muchas otras herramientas.  
  
 Los artículos de esta parte de la documentación proporcionan instrucciones y procedimientos recomendados para las características más importantes y técnicas de alto nivel para escribir programas modernos de C\+\+.  
  
-   [Compatibilidad con las características de C\+\+11\/14\/17](../cpp/support-for-cpp11-14-17-features-modern-cpp.md)  
  
-   [Sistema de tipos de C\+\+](../cpp/cpp-type-system-modern-cpp.md)  
  
-   [Inicialización uniforme y constructores de delegación](../cpp/uniform-initialization-and-delegating-constructors.md)  
  
-   [Duración de objetos y administración de recursos](../cpp/object-lifetime-and-resource-management-modern-cpp.md)  
  
-   [Recursos propios de los objetos \(RAII\)](../cpp/objects-own-resources-raii.md)  
  
-   [Punteros inteligentes](../cpp/smart-pointers-modern-cpp.md)  
  
-   [Pimpl para encapsulación en tiempo de compilación](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)  
  
-   [Contenedores](../cpp/containers-modern-cpp.md)  
  
-   [Algoritmos](../cpp/algorithms-modern-cpp.md)  
  
-   [Formato de cadena y de E\/S](../cpp/string-and-i-o-formatting-modern-cpp.md)  
  
-   [Controlar errores y excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)  
  
-   [Portabilidad en los límites de ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)  
  
 Para más información, consulte el artículo de StackOverflow sobre [qué giros de C\+\+ quedan desusados en C\+\+11](http://go.microsoft.com/fwlink/?LinkId=402836)  
  
## Vea también  
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)   
 [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)