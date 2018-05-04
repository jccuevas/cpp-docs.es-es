---
title: Errores y control de excepciones (C++ moderno) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5eab4199415974c995aa9b71ad53db41b7695827
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="errors-and-exception-handling-modern-c"></a>Controlar errores y excepciones (C++ moderno)
En C++ moderno, en la mayoría de los escenarios, la mejor manera para notificar y controlar los errores lógicos y errores en tiempo de ejecución es utilizar excepciones. Esto es especialmente cierto cuando la pila puede contener varias llamadas de función entre la función que detecta el error y la función que tiene el contexto para saber cómo controlarla. Las excepciones proporcionan una manera formal y bien definida para el código que detecta errores para pasar la información de la pila de llamadas.  
  
 Errores de programa generalmente se dividen en dos categorías: errores de lógica que causadas por programación errores, por ejemplo, un error "índice fuera del intervalo" y los errores en tiempo de ejecución que están fuera del control del programador, por ejemplo, un "servicio de red no está disponible" error. Informe de errores se administra en la programación de estilo C y en COM, devolviendo un valor que representa un código de error o un código de estado para una función determinada, o estableciendo una variable global que el llamador, opcionalmente, puede recuperar después de cada llamada de función para ver Si se han notificado errores. Por ejemplo, la programación COM usa el valor devuelto HRESULT para comunicar errores al llamador, y la API de Win32 tiene la función GetLastError para recuperar el último error devuelto por la pila de llamadas. En ambos casos, es al llamador que reconoce el código y responder a ella, según corresponda. Si el llamador no controla explícitamente el código de error, el programa podría bloquearse sin previo aviso o continuar ejecutar con los datos incorrectos y producir resultados incorrectos.  
  
 Las excepciones son las preferidas en C++ moderno por las razones siguientes:  
  
-   Una excepción fuerza el código de llamada para reconocer una condición de error y controlarla. Las excepciones no controladas detienen la ejecución del programa.  
  
-   Una excepción salta hasta el punto en la pila de llamadas que puede controlar el error. Funciones intermedias pueden dejar que la excepción se propaguen. No tiene coordinarse con otras capas.  
  
-   El mecanismo desenredo de pila de excepción destruye todos los objetos de ámbito según las reglas bien definidas después de que se produce una excepción.  
  
-   Una excepción permite una separación clara entre el código que detecta el error y el código que controla el error.  
  
 El siguiente ejemplo simplificado muestra la sintaxis necesaria para producir y detectar excepciones en C++.  
  
```cpp  
#include <stdexcept>  
#include <limits>  
#include <iostream>  
  
using namespace std;  
class MyClass  
{  
public:  
   void MyFunc(char c)  
   {  
      if(c < numeric_limits<char>::max())  
         throw invalid_argument("MyFunc argument too large.");  
      //...  
   }  
};  
  
int main()  
{  
   try  
   {  
      MyFunc(256); //cause an exception to throw  
   }  
  
   catch(invalid_argument& e)  
   {  
      cerr << e.what() << endl;  
      return -1;  
   }  
   //...  
   return 0;  
}  
  
```  
  
 Las excepciones de C++ son similares a las en lenguajes como C# y Java. En el `try` bloquear, si una excepción es *produce* será *detectó* por la primera asociados `catch` bloque cuyo tipo coincide con el de la excepción. En otras palabras, salta la ejecución de la `throw` instrucción para el `catch` instrucción. Si no se encuentra ningún bloque catch utilizable, `std::terminate` se invoca y el programa se cierra. En C++, se puede producir cualquier tipo; Sin embargo, se recomienda que produce un tipo que derive directa o indirectamente de `std::exception`. En el ejemplo anterior, el tipo de excepción, [invalid_argument](../standard-library/invalid-argument-class.md), se define en la biblioteca estándar en el [ \<stdexcept >](../standard-library/stdexcept.md) archivo de encabezado. C++ no proporciona y no requiere un `finally` bloque para asegurarse de que todos los recursos se liberan si se produce una excepción. La adquisición de recursos es la expresión de inicialización (RAII), que usa punteros inteligentes, proporciona la funcionalidad necesaria para la limpieza de recursos. Para obtener más información, consulte [Cómo: diseño de seguridad de las excepciones](../cpp/how-to-design-for-exception-safety.md). Para obtener información sobre el mecanismo desenredo de pila en C++, vea [excepciones y desenredo de pila](../cpp/exceptions-and-stack-unwinding-in-cpp.md).  
  
## <a name="basic-guidelines"></a>Directrices básicas  
 Control de errores sólido es un desafío en cualquier lenguaje de programación. Aunque las excepciones ofrecen varias características que admiten el control de errores buena, no todo el trabajo por usted. Para obtener los beneficios del mecanismo de excepciones, impiden que las excepciones en cuenta al diseñar el código.  
  
-   Utilice aserciones para comprobar los errores que nunca deben producirse. Usar excepciones para comprobar si hay errores que pueden producirse, por ejemplo, errores de validación de entrada en parámetros de funciones públicas. Para obtener más información, vea la sección titulada **excepciones vs. Las aserciones de**.  
  
-   Utilizar excepciones cuando el código que controla el error se podría separado del código que detecta el error por uno o más llamadas a funciones que intervengan. Considere la posibilidad de usar códigos de error en su lugar en bucles esenciales para el rendimiento al código que controle el error está estrechamente asociadas al código que lo detecta. 
  
-   Para todas las funciones que podrían producir o se propaga una excepción, proporcione una de las garantías de excepción: la garantía segura, la garantía básica o la garantía nothrow (noexcept). Para obtener más información, consulte [Cómo: diseño de seguridad de las excepciones](../cpp/how-to-design-for-exception-safety.md).  
  
-   Producir excepciones por valor, detectarlas por referencia. No detectar no puede controlar. 
  
-   No use las especificaciones de excepción, que están en desuso en C ++ 11. Para obtener más información, vea la sección titulada **especificaciones de excepciones y noexcept**.  
  
-   Usar tipos de excepción de la biblioteca estándar cuando se aplican. Derivar tipos de excepción personalizada desde el [clase exception](../standard-library/exception-class.md) jerarquía.  
  
-   No permitir excepciones de escape de destructores o funciones de desasignación de memoria.  
  
## <a name="exceptions-and-performance"></a>Excepciones y rendimiento  
 El mecanismo de excepción tiene un rendimiento muy pocos costo si se inicia ninguna excepción. Si se produce una excepción, el costo del recorrido de pila y desenredado es aproximadamente comparable con el costo de una llamada de función. Estructuras de datos adicionales son necesarias para realizar el seguimiento de la pila de llamadas tras una `try` instrucciones adicionales son necesarios para desenredar la pila si se produce una excepción y se escribe el bloque. Sin embargo, en la mayoría de los escenarios, el costo en rendimiento y consumo de memoria no es significativo. Los efectos adversos de excepciones en el rendimiento es probable que sean significativas sólo en sistemas muy restringidas por la memoria o en rendimiento crítico bucles donde es probable que se realizan con regularidad un error y el código para controlar está asociado estrechamente con el código que lo notifica. En cualquier caso, es imposible saber el costo real de excepciones sin necesidad de generación de perfiles y medir. Incluso en los pocos casos cuando el costo es importante, puede pesar, con la mayor exactitud, mantenimiento más fácil y otras ventajas que se proporcionan con una directiva de excepción bien diseñada.  
  
## <a name="exceptions-vs-assertions"></a>Excepciones frente a las aserciones  
 Excepciones y las aserciones son dos mecanismos diferentes para detectar errores en tiempo de ejecución en un programa. Utilice aserciones para probar condiciones de durante el desarrollo que nunca debe ser true si todo el código es correcto. No hay ningún punto de control de este tipo de error con una excepción porque el error indica que algo en el código debe corregirse y no representa una condición de que el programa debe recuperarse en tiempo de ejecución. Una aserción detiene la ejecución en la instrucción que puede inspeccionar el estado del programa en el depurador; una excepción continúa la ejecución desde el primer controlador catch correspondiente. Usar excepciones para comprobar las condiciones de error que pueden producirse en tiempo de ejecución, incluso si el código es correcto, por ejemplo, "archivo no encontrado" o "memoria insuficiente." Puede recuperar estas condiciones, incluso si la recuperación solo enviará un mensaje en un registro y finaliza el programa. Compruebe siempre los argumentos para funciones públicas mediante el uso de excepciones. Incluso si la función es libre de errores, no tendrá un control completo sobre los argumentos que un usuario podría pasar a él.  
  
## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Excepciones de C++ frente a excepciones SEH de Windows  
 Programas de C y C++ pueden utilizar el mecanismo de (SEH) en el sistema operativo Windows de control de excepciones estructurado. Los conceptos de SEH son similares a las excepciones de C++, salvo que usa SEH el `__try`, `__except`, y `__finally` construye en lugar de `try` y `catch`. En Visual C++, las excepciones de C++ se implementan para SEH. Sin embargo, cuando se escribe código de C++, use la sintaxis de excepción de C++.  
  
 Para obtener más información acerca de SEH, consulte [control de excepciones estructurado (C/C ++)](../cpp/structured-exception-handling-c-cpp.md).  
  
## <a name="exception-specifications-and-noexcept"></a>Noexcept y especificaciones de excepciones  
 Especificaciones de excepciones se incluyeron en C++ como una manera de especificar las excepciones que se podría producir una función. Sin embargo, las especificaciones de excepción resultó problemáticas en la práctica y están en desuso en el estándar C ++ 11 borrador. Se recomienda que no utilicen las especificaciones de excepción excepto `throw()`, que indica que la función no permite ninguna excepción se escape. Si tiene que utilizar las especificaciones de excepción del tipo `throw(` *tipo*`)`, tenga en cuenta que Visual C++ se sale de estándar de ciertas formas. Para obtener más información, consulte [especificaciones de excepciones (throw)](../cpp/exception-specifications-throw-cpp.md). El `noexcept` especificador se introdujo en C ++ 11 como la alternativa preferida para `throw()`.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: interfaz entre código excepcional y no excepcional](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)   
 [Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
