---
title: "Notaci&#243;n de conversi&#243;n e introducci&#243;n de safe_cast&lt;&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "convertir"
  - "conversiones de estilo C y /clr, motivación para una nueva notación de conversión"
  - "safe_cast (palabra clave) [C++]"
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Notaci&#243;n de conversi&#243;n e introducci&#243;n de safe_cast&lt;&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La notación de conversión ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 Modificar una estructura existente es una experiencia diferente y más difícil que elaborar la estructura inicial.  Hay un grado de libertad menor y la solución tiende a ser un compromiso entre una reestructuración ideal y lo que resulta factible dadas las dependencias estructurales existentes.  
  
 La extensión de lenguaje es otro ejemplo.  Al principio de los años 90, cuando la programación orientada a objetos se convirtió en un paradigma importante, se hizo urgente la necesidad de una utilidad de conversión en tipos inferiores con seguridad de tipos en C\+\+.  La conversión en tipos inferiores es la conversión explícita de usuario de un puntero de clase base, una referencia a un puntero o una referencia de una clase derivada.  La conversión en tipos inferiores requiere una conversión explícita.  El motivo de ello es que el tipo real del puntero de clase base es un aspecto del motor en tiempo de ejecución; por lo tanto, el compilador no puede comprobarlo.  En otras palabras, una utilidad de conversión en tipos inferiores, al igual que una llamada de función virtual, requiere una forma de resolución dinámica.  Esto plantea dos preguntas:  
  
-   ¿Por qué debe ser necesaria una conversión de tipos inferiores en el paradigma orientado a objetos?  ¿No es suficiente el mecanismo de función virtual?  Es decir, ¿por qué no se puede afirmar que cualquier necesidad de conversión de tipos inferiores \(o conversión de cualquier tipo\) es un error de diseño?  
  
-   ¿Por qué debería ser un problema la compatibilidad de una conversión de tipos inferiores en C\+\+?  Después de todo, ¿es acaso un problema en lenguajes orientados a objetos como Smalltalk \(o, por consiguiente, Java y C\#\)?  ¿Qué pasa con C\+\+ que dificulta la compatibilidad con la utilidad de conversión en tipos inferiores?  
  
 Una función virtual representa un algoritmo dependiente del tipo que es común a una familia de tipos. \(No estamos teniendo en cuenta las interfaces, que no se admiten en ISO C\+\+ pero que están disponibles en la programación de CLR y que representan una alternativa de diseño interesante.\)  El diseño de esa familia se representa normalmente mediante una jerarquía de clases en la que hay una clase base abstracta que declara la interfaz común \(las funciones virtuales\) y un conjunto de clases derivadas concretas que representan los tipos de familia reales en el dominio de aplicación.  
  
 Una jerarquía `Light` es un dominio de aplicación de imágenes generadas por equipo \(CGI, Computer Generated Imagery\), que tendrán, por ejemplo, atributos comunes como `color`, `intensity`, `position`, `on`, `off`, etc.  Se pueden controlar varias luces mediante la interfaz común sin tener que preocuparse de que una luz en particular sea un foco de luz, una luz direccional, una luz no direccional \(piense en el sol\) o quizá una luz de la puerta de un establo.  En este caso, la conversión en tipos inferiores a un tipo de luz en particular para que ejerza su interfaz virtual resulta innecesaria.  Sin embargo, en un entorno de producción la velocidad resulta esencial.  Se puede realizar una conversión en tipos inferiores e invocar a cada método de forma explícita si al hacerlo se puede llevar a cabo la ejecución en línea de las llamadas en lugar de utilizar el mecanismo virtual.  
  
 Así que una razón para la conversión en tipos inferiores en C\+\+ es suprimir el mecanismo virtual a cambio de una ganancia significativa en el rendimiento en tiempo de ejecución. \(Observe que la automatización de esta optimización manual es un área activa de investigación.  Sin embargo, es más difícil resolver que reemplazar el uso explícito de la palabra clave `register` o `inline`.\)  
  
 Una segunda razón para la conversión en tipos inferiores es la consecuencia de la doble naturaleza del polimorfismo.  Una manera de pensar en el polimorfismo es dividirlo en un par de formatos pasivo y dinámico.  
  
 Una invocación virtual \(y una utilidad de conversión en tipos inferiores\) representa los usos dinámicos del polimorfismo: uno es realizar una acción basada en el tipo real del puntero de clase base en esa instancia concreta en la ejecución del programa.  
  
 La asignación de un objeto de clase derivada a su puntero de clase base es, no obstante, una forma pasiva de polimorfismo; es utilizar el polimorfismo como mecanismo de transporte.  Éste es el uso principal de `Object`, por ejemplo, en programación con CLR pregenérica.  Cuando se utiliza de forma pasiva, el puntero de clase base elegido para el transporte y el almacenamiento proporciona normalmente una interfaz que es demasiado abstracta.  Por ejemplo, `Object` proporciona aproximadamente cinco métodos a través de su interfaz; cualquier comportamiento más específico requiere una conversión en tipos inferiores explícita.  Por ejemplo, si deseamos ajustar el ángulo de nuestro foco de luz o su porcentaje de reducción, tendríamos que convertirlo en un tipo inferior de forma explícita.  Una interfaz virtual dentro de una familia de subtipos no puede ser, desde un punto de vista práctico, un superconjunto de todos los métodos posibles de sus numerosos elementos secundarios, por lo que se necesita siempre una utilidad de conversión en tipos inferiores dentro de un lenguaje orientado a objetos.  
  
 Si se necesita una utilidad de conversión en tipos inferiores segura en un lenguaje orientado a objetos, ¿por qué ha tardado tanto C\+\+ en agregar una?  El problema es cómo hacer que esté disponible la información acerca del tipo en tiempo de ejecución del puntero.  En el caso de una función virtual, el compilador establece la información en tiempo de ejecución en dos partes:  
  
-   El objeto de clase contiene un miembro de puntero de tabla virtual adicional \(ya sea al principio o al final del objeto de clase; lo que ya es interesante de por sí\) dirigido a la tabla virtual adecuada.  Por ejemplo, un objeto de foco de luz se dirige a una tabla virtual de foco de luz, una luz direccional, una tabla virtual de luz direccional, etc.  
  
-   Cada función virtual tiene una ranura fija asociada en la tabla, y la instancia real que se va a invocar está representada por la dirección almacenada dentro de la tabla.  Por ejemplo, el destructor `Light` virtual se puede asociar a la ranura 0, `Color` a la ranura 1, etc.  Se trata de una estrategia eficaz aunque inflexible porque se establece en el tiempo de compilación y representa una sobrecarga mínima.  
  
 El problema es cómo hacer que esté disponible la información de tipos para el puntero sin cambiar el tamaño de los punteros de C\+\+, agregando una segunda dirección o agregando directamente alguna codificación de tipos.  Esto no era aceptable para los programadores \(y programas\) que decidían no utilizar el paradigma orientado a objetos, que era todavía la comunidad de usuarios predominante.  Otra posibilidad era introducir un puntero especial para tipos de clases polimórficas, pero esto sería confuso y dificultaría la intercombinación de los dos, especialmente en cuestiones de aritmética de punteros.  Tampoco habría sido aceptable mantener una tabla en tiempo de ejecución que asociara cada puntero al tipo asociado actualmente y lo actualizara dinámicamente.  
  
 El problema reside, por lo tanto, en un par de comunidades de usuarios que tienen aspiraciones de programación diferentes aunque legítimas.  La solución debe ser un compromiso entre ambas comunidades, que les permita no solamente lograr sus aspiraciones sino también interoperar.  Esto significa que las soluciones ofrecidas por ambas partes no sean viables probablemente y que finalmente la solución implementada no sea una buena solución.  La resolución real gira en torno a la definición de una clase polimórfica: una clase polimórfica es una clase que contiene una función virtual.  Una clase polimórfica admite una conversión en tipos inferiores con seguridad de tipos y dinámica.  Esto resuelve el problema de mantener\-el\-puntero\-como\-dirección porque todas las clases polimórficas contienen ese miembro de puntero adicional en su tabla virtual asociada.  Por consiguiente, la información de tipo asociada se puede almacenar en una estructura de tabla virtual expandida.  El costo de la conversión en tipos inferiores con seguridad de tipos está \(prácticamente\) localizada para los usuarios de la utilidad.  
  
 El siguiente problema acerca de la conversión en tipos inferiores con seguridad de tipos era su sintaxis.  Dado que se trata de una conversión de tipos, la propuesta original al comité de ISO C\+\+ utilizó la sintaxis de la conversión de tipos sencilla, como en este ejemplo:  
  
```  
spot = ( SpotLight* ) plight;  
```  
  
 pero el comité la rechazó porque no permitía al usuario controlar el costo de la conversión de tipos.  Si la conversión en tipos inferiores con seguridad de tipos tiene la misma sintaxis que la notación de conversión anterior no segura pero estática, entonces se convierte en una sustitución y el usuario no tiene la capacidad de eliminar la sobrecarga en tiempo de ejecución cuando no es necesaria y es quizá demasiado costosa.  
  
 En general, en C\+\+, hay siempre un mecanismo mediante el que se suprime la funcionalidad admitida por el compilador.  Por ejemplo, podemos desactivar el mecanismo virtual utilizando el operador de ámbito de clase \(`Box::rotate(angle)`\) o invocando el método virtual mediante un objeto de clase \(en lugar de un puntero o una referencia de dicha clase\).  Esta última supresión no es necesaria para el lenguaje pero es una cualidad de la cuestión de la implementación, similar a la supresión de la construcción de un temporal en una declaración del formato:  
  
```  
// compilers are free to optimize away the temporary  
X x = X::X( 10 );  
```  
  
 Se retomó la propuesta para examinarla más detalladamente y se tuvieron en cuenta varias notaciones alternativas, y la que se volvió a exponer al comité era del formato \(`?type`\), lo que indicaba su naturaleza indeterminada, es decir, dinámica.  Esto daba al usuario la capacidad de cambiar entre dos formatos, estático o dinámico, pero nadie estaba muy contento por ello.  Así que se envió de nuevo a la mesa de dibujo.  La tercera notación y la más correcta es el estándar actual `dynamic_cast<type>`, que se generalizó en un conjunto de cuatro notaciones de conversión de nuevo estilo.  
  
 En ISO C\+\+, `dynamic_cast` devuelve `0` cuando se aplica a un tipo de puntero inadecuado e inicia una excepción `std::bad_cast` cuando se aplica a un tipo de referencia.  En Extensiones administradas para C\+\+, la aplicación de `dynamic_cast` a un tipo de referencia administrado \(debido a la representación de su puntero\) devolvía siempre `0`.  Se introdujo `__try_cast<type>` como análogo a la variante de inicio de excepción de `dynamic_cast`, con la excepción de que inicia `System::InvalidCastException` si la conversión no es correcta.  
  
```  
public __gc class ItemVerb;  
public __gc class ItemVerbCollection {  
public:  
   ItemVerb *EnsureVerbArray() [] {  
      return __try_cast<ItemVerb *[]>  
         (verbList->ToArray(__typeof(ItemVerb *)));  
   }  
};  
```  
  
 En la nueva sintaxis, `__try_cast` se ha reconvertido a `safe_cast`.  A continuación se muestra el mismo fragmento de código en la nueva sintaxis:  
  
```  
public ref class ItemVerb;  
public ref class ItemVerbCollection {  
public:  
   array<ItemVerb^>^ EnsureVerbArray() {  
      return safe_cast<array<ItemVerb^>^>  
         ( verbList->ToArray( ItemVerb::typeid ));  
   }  
};  
```  
  
 En el mundo administrado, es importante permitir el código comprobable dominando la capacidad de los programadores de convertir entre tipos que dejan código sin comprobar.  Éste es un aspecto crítico del paradigma de programación dinámica representado por la nueva sintaxis.  Por esta razón, las instancias de conversiones en antiguos estilos se reconvierten internamente en conversiones en tiempo de ejecución, para que, por ejemplo:  
  
```  
// internally recast into the   
// equivalent safe_cast expression above  
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );   
```  
  
 Por otra parte, como el polimorfismo proporciona un modo activo y otro pasivo, a veces es necesario realizar una conversión en tipos inferiores simplemente para obtener acceso a la API no virtual de un subtipo.  Esto puede suceder, por ejemplo, con los miembros de una clase que desea dirigirse a cualquier tipo dentro de la jerarquía \(polimorfismo pasivo como mecanismo de transporte\) pero para el que se conoce la instancia real dentro del contexto de un programa concreto.  En este caso, tener una comprobación en tiempo de ejecución de la conversión de tipos puede ser una sobrecarga inaceptable.  Si la nueva sintaxis es servir como el lenguaje de programación para sistemas administrados, debe proporcionar algunos medios que permitan la conversión en tipos inferiores en tiempo de compilación \(es decir, estática\).  Ése es el motivo por el que la aplicación de la notación `static_cast` puede seguir siendo una conversión en tipos inferiores en tiempo de compilación:  
  
```  
// ok: cast performed at compile-time.   
// No run-time check for type correctness  
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));  
```  
  
 El problema es que no hay manera de garantizar que el programador que realiza `static_cast` es correcto y bien intencionado; es decir, que no hay manera de exigir que el código administrado sea comprobable.  Éste es un tema más urgente para el paradigma de programación dinámica que para la nativa, pero no basta en un lenguaje de programación de sistemas para deshabilitar la capacidad del usuario de pasar de una conversión estática a una en tiempo de ejecución y viceversa.  
  
 Sin embargo, existe una trampa y una dificultad de rendimiento en la nueva sintaxis.  En la programación nativa, no hay ninguna diferencia en el rendimiento entre la notación de conversión de antiguo estilo y la notación `static_cast` de nuevo estilo.  Pero en la nueva sintaxis, la notación de conversión de antiguo estilo es significativamente más costosa que el uso de la notación `static_cast` de nuevo estilo.  El motivo es que el compilador transforma internamente el uso de la notación de antiguo estilo en una comprobación en tiempo de ejecución que produce una excepción.  Asimismo, también cambia el perfil de ejecución del código porque provoca una excepción no detectada y detiene la aplicación, quizá de forma prudente, pero este mismo error no iniciaría esta excepción si se utilizara la notación `static_cast`.  Se podría alegar que esto ayuda a los usuarios a utilizar la notación de nuevo estilo.  Pero sólo cuando se produce un error; si no, sólo hará que los programas que utilizan la notación de antiguo estilo funcionen mucho más lentamente sin saber visiblemente el motivo, de forma similar a las siguientes dificultades de los programadores de C:  
  
```  
// pitfall # 1:   
// initialization can remove a temporary class object,   
// assignment cannot  
Matrix m;  
m = another_matrix;  
  
// pitfall # 2: declaration of class objects far from their use  
Matrix m( 2000, 2000 ), n( 2000, 2000 );  
if ( ! mumble ) return;  
```  
  
## Vea también  
 [Cambio general en el lenguaje](../dotnet/general-language-changes-cpp-cli.md)   
 [Conversiones de estilo C con \/clr \(C\+\+\/CLI\)](../windows/c-style-casts-with-clr-cpp-cli.md)   
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)