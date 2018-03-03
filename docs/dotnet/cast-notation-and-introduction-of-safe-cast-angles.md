---
title: "Notación de conversión e introducción de safe_cast&lt; &gt; | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80d1a6e8b1a1691b4e76bfdc1232c95c22d01408
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>Notación de conversión e introducción de safe_cast&lt;&gt;
La notación de conversión ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 Modificar una estructura existente es una experiencia diferente y más difícil que elaborar la estructura inicial. Hay menos grados de libertad y la solución tiende a es un compromiso entre una reestructuración ideal y lo que resulta factible dadas las dependencias estructurales existentes.  
  
 Extensión del lenguaje es otro ejemplo. En la década de 1990 temprano como programación orientada a se convirtió en un paradigma importante, la necesidad de una utilidad de conversión en tipos inferiores con seguridad de tipos en C++ se hizo urgente. Convertir a tipo heredado es la conversión explícita del usuario de un puntero de clase base o una referencia a un puntero o referencia de una clase derivada. Convertir a tipo heredado requiere una conversión explícita. La razón es que el tipo real del puntero de clase base es un aspecto del tiempo de ejecución; el compilador, por tanto, no puede protegerlo. O bien, para volver a formular, una instalación downcast, al igual que una llamada de función virtual, requiere alguna forma de resolución dinámica. Esto provoca dos preguntas:  
  
-   ¿Por qué deberían tipos inferiores que sea necesario en el paradigma orientado a objetos? ¿No es el mecanismo de función virtual suficiente? Es decir, ¿por qué no se puede afirmar que cualquier necesidad de una conversión en tipos inferiores (o una conversión de cualquier tipo) es un error de diseño?  
  
-   ¿Por qué debería ser un problema en C++ compatibilidad de una conversión en tipos inferiores? ¿Después de todo, no es un problema en lenguajes orientados a objetos como Smalltalk (o, por consiguiente, Java y C#)? ¿Qué es información acerca de C++ que dificulta la compatibilidad con una instalación downcast difícil?  
  
 Una función virtual representa un algoritmo dependiente de tipo común a una familia de tipos. (No estamos considerando interfaces, que no son compatibles con ISO C++ pero que están disponibles en la programación de CLR y que representan una alternativa de diseño interesante). El diseño de esa familia se representa normalmente por una jerarquía de clases en el que hay una clase base abstracta que declara la interfaz común (las funciones virtuales) y un conjunto de clases derivadas concretas que representan los tipos de familia reales en la aplicación dominio.  
  
 A `Light` jerarquía en un dominio de aplicación de equipo genera imágenes (CGI), por ejemplo, tendrá los atributos comunes como `color`, `intensity`, `position`, `on`, `off`, y así sucesivamente. Uno puede controlar varias luces mediante la interfaz común sin preocuparse de si una luz en particular es un foco de luz, una luz direccional, una luz no direccional (piense en el sol) o quizá una luz de la puerta de la cortina. En este caso, la conversión a un tipo determinado de luz ejercer su interfaz virtual no es necesario. Sin embargo, en un entorno de producción, velocidad es fundamental. Uno podría downcast e invocar explícitamente cada método si al hacerlo se puede realizar la ejecución en línea de las llamadas en lugar de utilizar el mecanismo virtual.  
  
 Por lo tanto, una razón para convertirlo en C++ es suprimir el mecanismo virtual a cambio de una mejora significativa del rendimiento en tiempo de ejecución. (Tenga en cuenta que la automatización de esta optimización manual es un área activa de investigación. Sin embargo, resulta más difícil de resolver que reemplazar el uso explícito de la `register` o `inline` (palabra clave).)  
  
 Un segundo motivo para downcast queda fuera de la doble naturaleza del polimorfismo. Una manera de pensar en el polimorfismo se se divide en un par pasivo y dinámico de formularios.  
  
 Una invocación virtual (y una utilidad de conversión en tipos inferiores) representan los usos dinámicos del polimorfismo: uno está realizando una acción según el tipo real del puntero de clase base en esa instancia concreta en la ejecución del programa.  
  
 Asignación de un objeto de clase derivada a su puntero de clase base, sin embargo, es una forma pasiva de polimorfismo; que está usando el polimorfismo como mecanismo de transporte. Este es el uso principal de `Object`, por ejemplo, en la programación de CLR genérico previamente. Cuando se utiliza de forma pasiva, el puntero de clase base elegido para el transporte y almacenamiento normalmente ofrece una interfaz que es demasiado abstracta. `Object`, por ejemplo, proporciona aproximadamente cinco métodos a través de su interfaz; cualquier comportamiento más específico requiere explícito downcast. Por ejemplo, si desea ajustar el ángulo de nuestro foco de luz o su porcentaje de reducción, tendríamos que convertirlo explícitamente. Una interfaz virtual dentro de una familia de subtipos desde no puede ser un superconjunto de todos los métodos posibles de sus numerosos elementos secundarios y, por lo que siempre se necesitarán una utilidad de conversión en tipos inferiores dentro de un lenguaje orientado a objetos.  
  
 Si una caja fuerte downcast facility es necesario en un lenguaje orientado a objetos, a continuación, ¿por qué tarda C++ tanto para agregar uno? El problema está en cómo hacer que esté disponible la información acerca del tipo de tiempo de ejecución del puntero. En el caso de una función virtual, la información de tiempo de ejecución se configura en dos partes por el compilador:  
  
-   El objeto de clase contiene un miembro de puntero de tabla virtual adicional (ya sea al principio o al final del objeto de clase; que tiene un historial interesante por sí misma) relacionado con la tabla virtual adecuada. Por ejemplo, un objeto de spotlight direcciones una tabla virtual de servicios, una luz direccional, una tabla virtual claro direccional etc.  
  
-   Cada función virtual tiene asociada una ranura en la tabla fija y la instancia real para invocar está representada por la dirección almacenada dentro de la tabla. Por ejemplo, el virtual `Light` destructor puedan estar asociado a la ranura 0, `Color` con la ranura 1 y así sucesivamente. Se trata de una estrategia eficaz aunque inflexible porque está configurado en tiempo de compilación y representa una sobrecarga mínima.  
  
 El problema, a continuación, se muestra cómo realizar la información de tipo para el puntero sin cambiar el tamaño de los punteros de C++, agregando una segunda dirección o agregando directamente algún tipo de codificación de tipo. Esto no es aceptable para los programadores (y programas) que decidir no utilizar el paradigma orientado a objetos - que aún se estaba ejecutando la Comunidad de usuarios predominante. Otra posibilidad era introducir un puntero especial para tipos de clases polimórficas, pero esto sería confuso y dificultar la mezcla entre los dos, especialmente con problemas de la aritmética de puntero. También no sería aceptable para mantener una tabla en tiempo de ejecución que asocia cada puntero al tipo asociado actualmente y lo actualizara dinámicamente.  
  
 El problema, a continuación, es un par de comunidades de usuarios que tienen aspiraciones de programación diferentes aunque legítimas. La solución debe ser un compromiso entre las dos comunidades, que les permita no solo su aspiración pero la capacidad de interactuar. Esto significa que las soluciones ofrecidas por ambos lados suelen ser factible y la solución se implementa finalmente a ser inferior a perfecto. La resolución real gira en torno a la definición de una clase polimórfica: una clase polimórfica es aquel que contiene una función virtual. Una clase polimórfica admite un conversión en tipos inferiores de seguridad de tipos dinámico. Así resuelve el problema de mantener el-puntero-como-dirección porque todas las clases polimórficas contienen a ese miembro de puntero adicional a su tabla virtual asociada. La información de tipo asociado, por lo tanto, se puede almacenar en una estructura de tabla virtual expandida. El costo de la seguridad de tipos de conversión en tipos inferiores (casi) se adapta a los usuarios de la utilidad.  
  
 El siguiente problema con la conversión en tipos inferior con seguridad de tipos era su sintaxis. Dado que es una conversión de tipos, la propuesta original al Comité de ISO C++ utilizó la sintaxis de conversión de tipos sencilla, como en este ejemplo:  
  
```  
spot = ( SpotLight* ) plight;  
```  
  
 pero esto fue rechazado por el Comité porque no permitió al usuario controlar el costo de la conversión. Si la conversión en tipos inferiores de seguridad de tipos dinámica tiene la misma sintaxis que la palabra clave unsafe anteriormente pero estático notación de conversión, entonces se convierte en una sustitución y el usuario no tiene capacidad para suprimir la sobrecarga de tiempo de ejecución cuando es necesaria y quizás demasiado costosa.  
  
 En general, en C++, siempre hay un mecanismo por el que se va a suprimir la funcionalidad admitida por el compilador. Por ejemplo, podemos volver desactiva el mecanismo virtual mediante el operador de ámbito de clase (`Box::rotate(angle)`) o invocando el método virtual a través de un objeto de clase (en lugar de un puntero o referencia de dicha clase). Esta última supresión no es necesario según el idioma, pero es un problema de implementación, similar a la supresión de la construcción de un archivo temporal en una declaración de la forma de calidad:  
  
```  
// compilers are free to optimize away the temporary  
X x = X::X( 10 );  
```  
  
 Para que se dirigirá de nuevo la propuesta para examinarla más detalladamente y se tuvieron en cuenta varias notaciones alternativas y lo vuelve al Comité tenía el formato (`?type`), que indica su indeterminado: es decir, la naturaleza dinámica. Esto daba al usuario la capacidad de alternar entre las dos formas: estáticas o dinámicas - pero nadie estaba muy contento con él. Por lo que vuelva al panel de dibujo. La notación terceros y correcta es ahora estándar `dynamic_cast<type>`, que se generalizó en un conjunto de cuatro notaciones de conversión de nuevo estilo.  
  
 En ISO C++, `dynamic_cast` devuelve `0` cuando se aplica a un tipo de puntero inadecuado e inicia un `std::bad_cast` excepción cuando se aplica a un tipo de referencia. En extensiones administradas para C++, aplicar `dynamic_cast` a un tipo de referencia administrado (debido a su representación de puntero) siempre devuelven `0`. `__try_cast<type>`se introdujo como análogo a la excepción producir variante de la `dynamic_cast`, salvo que produce `System::InvalidCastException` si se produce un error en la conversión.  
  
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
  
 En la nueva sintaxis, `__try_cast` se ha reasignado a una como `safe_cast`. Este es el mismo fragmento de código en la nueva sintaxis:  
  
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
  
 En el entorno administrado, es importante permitir el código comprobable limitando la capacidad de los programadores para convertir entre tipos de forma que deje el código no comprobable. Se trata de un aspecto crucial del paradigma de programación dinámico representado por la nueva sintaxis. Por este motivo, las instancias de conversiones de estilo antiguo se reasignado una internamente como conversiones en tiempo de ejecución, así que, por ejemplo:  
  
```  
// internally recast into the   
// equivalent safe_cast expression above  
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );   
```  
  
 Por otro lado, como el polimorfismo proporciona un activo y el modo pasivo, a veces es necesario realizar una conversión para obtener acceso a la API no virtual de un subtipo. Esto puede ocurrir, por ejemplo, con los miembros de una clase que desea dirigirse a cualquier tipo dentro de la jerarquía (polimorfismo pasivo como mecanismo de transporte) pero para el que se conoce la instancia real dentro de un contexto de programa en particular. En este caso, tener una comprobación en tiempo de ejecución de la conversión puede ser una sobrecarga inaceptable. Si la nueva sintaxis es servir como el lenguaje de programación de sistemas administrados, debe proporcionar algún medio de lo que permite un tiempo de compilación (es decir, estática) inferiores. Por eso la aplicación de la `static_cast` notación puede permanecer un tiempo de compilación de conversión en tipos inferiores:  
  
```  
// ok: cast performed at compile-time.   
// No run-time check for type correctness  
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));  
```  
  
 El problema es que no hay ninguna manera de garantizar que el programador que realiza el `static_cast` es correcto y bien intencionado; es decir, no hay ninguna manera para forzar que el código administrado que se pueda comprobar. Esto es un problema más urgente bajo el paradigma de programación dinámica que bajo nativo, pero no es suficiente en un sistema de programación idioma que no permite al usuario la capacidad para alternar entre un estático y la convierte en el tiempo de ejecución.  
  
 No hay una captura de rendimiento y una dificultad en la nueva sintaxis, sin embargo. En la programación nativa, no hay ninguna diferencia en el rendimiento entre la notación de conversión de estilo antiguo y el nuevo estilo `static_cast` notación. Pero en la nueva sintaxis, la notación de conversión de estilo antiguo es mucho más cara que el uso del nuevo estilo `static_cast` notación. La razón es que el compilador transforma internamente el uso de la notación de estilo antiguo en una comprobación en tiempo de ejecución que produce una excepción. Además, también cambia el perfil de ejecución del código porque hace que una excepción no detectada y detiene la aplicación, quizás con cuidado, pero el mismo error no iniciaría esta excepción si el `static_cast` se utiliza la notación. Se podría alegar que esto ayuda a los usuarios sobre cómo usar la notación de nuevo estilo. Pero sólo cuando se produce un error; en caso contrario, hará que los programas que utilizan la notación de estilo antiguo ejecutará mucho más lentamente sin saber visible por este motivo, similar a las dificultades de los programadores de C siguientes:  
  
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
  
## <a name="see-also"></a>Vea también  
 [Cambios del lenguaje general (C++ / CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [Conversiones de estilo C con /clr (C++ / CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)