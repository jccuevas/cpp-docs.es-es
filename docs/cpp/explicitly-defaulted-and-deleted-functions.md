---
title: "Explícitamente como valores predeterminados y las funciones eliminadas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73e1d52d1c13e2defa51a5cab9da625b75aac757
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Funciones establecidas como valor predeterminado y eliminadas explícitamente
En C++11, las funciones establecidas como valor predeterminado y eliminadas proporcionan un control explícito sobre si las funciones miembro especiales se generan automáticamente. Las funciones eliminadas también proporcionan un lenguaje simple para impedir que se realicen promociones de tipo problemáticas en argumentos de funciones de todos los tipos (funciones miembro especiales, así como funciones miembro normales y funciones no miembro) que podrían provocar una llamada a función no deseada.  
  
## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Ventajas de las funciones establecidas como valor predeterminado o eliminadas explícitamente  
 En C++, el compilador genera automáticamente el constructor predeterminado, el constructor de copias, el operador de asignación de copia y el destructor de un tipo si este no declara los suyos propios. Estas funciones se conocen como el *funciones miembro especiales*, y son lo que permite tipos simples definidos por el usuario en C++ se comportan como las estructuras en C. Es decir, puede crear, copiar y destruir sin ningún esfuerzo de codificación adicional. C++11 aporta semántica de movimiento al lenguaje y agrega el constructor de movimiento y el operador de asignación de movimiento a la lista de funciones miembro especiales que el compilador puede generar automáticamente.  
  
 Esto es útil en el caso de tipos simples, pero los tipos complejos suelen definir una o varias funciones miembro especiales por sí mismos, lo que puede impedir la generación automática de otras funciones miembro especiales. En la práctica:  
  
-   Si se declara explícitamente un constructor, no se genera automáticamente ningún constructor predeterminado.  
  
-   Si se declara explícitamente un destructor virtual, no se genera automáticamente ningún destructor predeterminado.  
  
-   Si se declara explícitamente un constructor de movimiento o un operador de asignación de movimiento, entonces:  
  
    -   No se genera automáticamente ningún constructor de copia.  
  
    -   No se genera automáticamente ningún operador de asignación de copia.  
  
-   Si se declara explícitamente un constructor de copia, un operador de asignación de copia, un constructor de movimiento, un operador de asignación de movimiento o un destructor, entonces:  
  
    -   No se genera automáticamente ningún constructor de movimiento.  
  
    -   No se genera automáticamente ningún operador de asignación de movimiento.  
  
> [!NOTE]
>  Además, el estándar C++11 especifica las reglas adicionales siguientes:  
>   
>  -   Si se declara explícitamente un constructor de copia o un destructor, la generación automática del operador de asignación de copia está desusada.  
> -   Si se declara explícitamente un operador de asignación de copia o un destructor, la generación automática del constructor de copia está desusada.  
>   
>  En ambos casos, Visual Studio sigue generando automáticamente las funciones necesarias de forma implícita y no emite ninguna advertencia.  
  
 Las consecuencias de estas reglas también pueden propagarse a las jerarquías de objetos. Por ejemplo, si por cualquier motivo una clase base no puede tener un constructor predeterminado al que se pueda llamar desde una clase derivada (es decir, un constructor `public` o `protected` que no toma ningún parámetro), una clase derivada de ella no puede generar automáticamente su propio constructor predeterminado.  
  
 Estas reglas pueden complicar la implementación de lo que deberían ser tipos sencillos definidos por el usuario y expresiones comunes de C++, como la creación de un tipo definido por el usuario que no se puede copiar declarando de forma privada el constructor de copia y el operador de asignación de copia y no definiéndolos.  
  
```  
struct noncopyable  
{  
  noncopyable() {};  
  
private:  
  noncopyable(const noncopyable&);  
  noncopyable& operator=(const noncopyable&);  
};  
```  
  
 Antes de C++11, este fragmento de código era la forma idiomática de los tipos que no se pueden copiar. Sin embargo, plantea varios problemas:  
  
-   El constructor de copia debe declararse de forma privada para ocultarlo, pero como se ha declarado plenamente, se impide la generación automática del constructor predeterminado. Tiene que definir explícitamente el constructor predeterminado si desea uno, aunque no haga nada.  
  
-   Aunque el constructor predeterminado definido de forma explícita no realice ninguna acción, el compilador lo considera no trivial. Es menos eficaz que un constructor predeterminado generado automáticamente e impide que `noncopyable` sea un verdadero tipo POD.  
  
-   Aunque el constructor de copia y el operador de asignación de copia estén ocultos para el código externo, las funciones miembro y los elementos friend de `noncopyable` aún pueden verlos y llamarlos. Si se han declarado pero no se han definido, al llamarlos se produce un error del vinculador.  
  
-   Aunque se trata de una expresión normalmente aceptada, la intención no está clara a menos que entienda todas las reglas de la generación automática de las funciones miembro especiales.  
  
 En C++11, la expresión que no se puede copiar se puede implementar de manera más sencilla.  
  
```  
struct noncopyable  
{  
  noncopyable() =default;  
  noncopyable(const noncopyable&) =delete;  
  noncopyable& operator=(const noncopyable&) =delete;  
};  
```  
  
 Observe cómo se resuelven los problemas con la expresión anterior a C++11:  
  
-   La generación del constructor predeterminado todavía se puede evitar declarando el constructor de copia, pero se puede volver a utilizar si se establece explícitamente como valor predeterminado.  
  
-   Las funciones miembro especiales establecidas como valor predeterminado explícitamente todavía se consideran triviales, por lo que no hay ninguna reducción del rendimiento y no se impide que `noncopyable` sea un verdadero tipo POD.  
  
-   El constructor de copia y el operador de asignación de copia son públicos pero se han eliminado. Es un error en tiempo de compilación definir o llamar a una función eliminada.  
  
-   La intención queda clara para cualquiera que entienda `=default` y `=delete`. No es necesario comprender las reglas de generación automática de funciones miembro especiales.  
  
 Existen expresiones similares para crear tipos definidos por el usuario que son no movibles, que solo pueden asignarse dinámicamente o que no se pueden asignar dinámicamente. Cada una de estas expresiones tiene implementaciones previas a C++11 que experimentan problemas similares, y que se resuelven de manera similar en C++11 mediante su implementación basada en funciones miembro especiales como valores predeterminados y eliminadas.  
  
## <a name="explicitly-defaulted-functions"></a>Funciones establecidas como valor predeterminado explícitamente  
 Puede establecer como valor predeterminado cualquiera de las funciones miembro especiales para establecer explícitamente que la función miembro especial usa la implementación predeterminada, definir la función miembro especial con un calificador de acceso no público o restablecer una función miembro especial cuya generación automática no pudo realizarse debido a otras circunstancias.  
  
 Una función miembro especial se establece como predeterminada declarándola como en este ejemplo:  
  
```  
struct widget  
{  
  widget()=default;  
  
  inline widget& operator=(const widget&);  
};  
  
inline widget& widget::operator=(const widget&) =default;  
```  
  
 Tenga en cuenta que puede establecer como valor predeterminado una función miembro especial fuera del cuerpo de una clase siempre y cuando se pueda insertar.  
  
 Debido a las ventajas de rendimiento que ofrecen las funciones miembro especiales triviales, se recomienda elegir funciones miembro especiales generadas automáticamente en lugar de cuerpos de función vacíos cuando se desee el comportamiento predeterminado. Se puede hacer si se establece explícitamente como valor predeterminado la función miembro especial o si no la declara (y tampoco declara otras funciones miembro especiales que impedirían que se generara automáticamente).  
  
## <a name="deleted-functions"></a>Funciones eliminadas  
 Es posible eliminar funciones miembro especiales, así como funciones miembro normales y funciones no miembro, para evitar que se definan o se llamen. La eliminación de funciones miembro especiales proporciona una forma más limpia de impedir que el compilador genere funciones miembro especiales que no se desean. La función se debe eliminar en cuanto se declara; no se puede eliminar después de la manera en que se puede declarar una función y establecerla como valor predeterminado más adelante.  
  
```  
struct widget  
{  
  // deleted operator new prevents widget from being dynamically allocated.  
  void* operator new(std::size_t) = delete;  
};  
```  
  
 La eliminación de funciones miembro normales o funciones no miembro impide que las promociones de tipo problemáticas llamen a una función no deseada. Esto funciona porque las funciones eliminadas siguen participando en la resolución de sobrecargas y proporcionan una mejor coincidencia que la función a la que se puede llamar después de que se promuevan los tipos. La llamada a función se resuelve en la función más específica, pero eliminada, y produce un error del compilador.  
  
```  
// deleted overload prevents call through type promotion of float to double from succeeding.  
void call_with_true_double_only(float) =delete;  
void call_with_true_double_only(double param) { return; }  
```  
  
 En el ejemplo anterior, observe que la llamada a `call_with_true_double_only` utilizando un argumento `float` produciría un error del compilador, pero la llamada a `call_with_true_double_only` con un argumento `int` no; en el caso de `int`, el argumento se promoverá de `int` a `double` y llamará correctamente a la versión e `double` de la función, aunque esto no sea lo que se esperaba. Para asegurarse de que cualquier llamada a esta función mediante un argumento que no sea double produce un error del compilador, se puede declarar una versión de plantilla de la función que se elimina.  
  
```  
template < typename T >  
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.  
  
void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.  
  
```