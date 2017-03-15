---
title: "Controlar errores y excepciones (C++ moderno) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controlar errores y excepciones (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En C++ moderno, en la mayoría de los escenarios, la mejor manera de comunicar y tratar errores lógicos y errores en tiempo de ejecución es utilizar las excepciones. Esto es especialmente cierto cuando la pila puede contener varias llamadas de función entre la función que detecta el error y la función que tiene el contexto para saber cómo tratarlo. Las excepciones proporcionan una manera formal y bien definida para el código que detecta errores para pasar la información de la pila de llamadas.  
  
 Errores de programa generalmente se dividen en dos categorías: errores de lógica causados por programación errores, por ejemplo, un error "índice fuera del intervalo" y errores de tiempo de ejecución que están fuera del control del programador, por ejemplo, un error "servicio no disponible de la red". Informe de errores se administra en la programación de estilo C y en COM, devolviendo un valor que representa un código de error o un código de estado para una función determinada, o estableciendo una variable global que el llamador, opcionalmente, puede recuperar después de cada llamada de función para ver si se han notificado errores. Por ejemplo, la programación COM utiliza el valor devuelto HRESULT para comunicar errores al llamador, y la API de Win32 tiene la función GetLastError para recuperar el último error que se ha informado de la pila de llamadas. En ambos casos, es al llamador que reconoce el código y responder adecuadamente. Si el llamador no controla explícitamente el código de error, el programa podría bloquearse sin advertencia, o seguir se ejecutan con datos erróneos y generar resultados incorrectos.  
  
 Las excepciones son las preferidas en C++ moderno por las razones siguientes:  
  
-   Una excepción fuerza el código de llamada para reconocer una condición de error y controlarla. Las excepciones no controladas detienen la ejecución del programa.  
  
-   Una excepción se salta hasta el punto en la pila de llamadas que puede controlar el error. Funciones intermedias pueden permitir que la excepción a propagar. No tienen que coordinar con otras capas.  
  
-   El mecanismo de desenredo de pila de excepción destruye todos los objetos de ámbito según las reglas bien definidas después de que se produce una excepción.  
  
-   Una excepción permite una separación clara entre el código que detecta el error y el código que controla el error.  
  
 El siguiente ejemplo simplificado muestra la sintaxis necesaria para iniciar y detectar excepciones en C++.  
  
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
  
 Las excepciones de C++ son similares a las de lenguajes como C# y Java. En el `try` Bloquear, si es una excepción *produce* será *detectada* por el primer asociado `catch` bloque cuyo tipo coincide con el de la excepción. En otras palabras, se salta la ejecución de la `throw` instrucción para el `catch` instrucción. Si no se encuentra ningún bloque catch utilizable, `std::terminate` se invoca y se cierra el programa. En C++, se puede producir cualquier tipo; Sin embargo, se recomienda que produzca un tipo que deriva directa o indirectamente de `std::exception`. En el ejemplo anterior, el tipo de excepción [invalid_argument](../standard-library/invalid-argument-class.md), se define en la biblioteca estándar de la [\< stdexcept>](../standard-library/stdexcept.md) archivo de encabezado. C++ no proporciona y no requiere un `finally` bloque para asegurarse de que todos los recursos se liberan si se produce una excepción. La adquisición de recursos es la expresión de inicialización (RAII), que utiliza punteros inteligentes, proporciona la funcionalidad necesaria para la limpieza de recursos. Para obtener más información, vea [Cómo: diseñar para la seguridad de excepción](../cpp/how-to-design-for-exception-safety.md). Para obtener información sobre el mecanismo de desenredo de pila en C++, vea [excepciones y desenredo de pila](../cpp/exceptions-and-stack-unwinding-in-cpp.md).  
  
## <a name="basic-guidelines"></a>Directrices básicas  
 Control de errores sólido es un desafío en cualquier lenguaje de programación. Aunque las excepciones proporcionan varias características que admiten el control de errores buena, no todo el trabajo por usted. Para obtener los beneficios del mecanismo de excepciones, las excepciones mientras tenga en cuenta al diseñar el código.  
  
-   Utilice aserciones para comprobar los errores que nunca deben producirse. Usar excepciones para comprobar los errores que pueden producirse, por ejemplo, errores de validación de entrada en parámetros de funciones públicas. Para obtener más información, vea la sección titulada **excepciones vs. Aserciones**.  
  
-   Utilice las excepciones cuando el código que controla el error se podría separado del código que detecta el error por una o más llamadas de función que intervienen. Considere la posibilidad de utilizar códigos de error en su lugar en bucles críticos de rendimiento al código que controle el error está estrechamente unido al código que detecta. Para obtener más información acerca de cuándo no usar excepciones, vea [(NOTINBUILD) cuando no utilice excepciones](http://msdn.microsoft.com/es-es/e810df8b-2217-4e81-bae5-02f0a69f1346).  
  
-   Para cada función que podría producir o propagar una excepción, proporcionan una de las garantías de excepción: la garantía segura, la garantía básica o la garantía nothrow (noexcept). Para obtener más información, vea [Cómo: diseñar para la seguridad de excepción](../cpp/how-to-design-for-exception-safety.md).  
  
-   Producir excepciones por valor, detectarlas por referencia. No se atrapan no puede controlar. Para obtener más información, consulte [directrices (NOTINBUILD) para producir y detectar excepciones (C++)](http://msdn.microsoft.com/es-es/0a9b0a3a-64c5-43f5-a080-fca69b89e839).  
  
-   No use las especificaciones de excepciones, que están en desuso en C ++ 11. Para obtener más información, vea la sección titulada **especificaciones de excepciones y noexcept**.  
  
-   Utilice tipos de excepción de la biblioteca estándar cuando se aplican. Derivar tipos de excepción personalizada desde el [clase exception](../standard-library/exception-class1.md) jerarquía. Para obtener más información, consulte [(NOTINBUILD) Cómo: utilizar los objetos de excepción estándar de biblioteca](http://msdn.microsoft.com/es-es/ad1fb785-ed4e-4d94-8e84-964353aed7b6).  
  
-   No permitir excepciones de escape de destructores o funciones de desasignación de memoria.  
  
## <a name="exceptions-and-performance"></a>Excepciones y rendimiento  
 El mecanismo de excepciones afectará al rendimiento mínimo si se produce ninguna excepción. Si se produce una excepción, el coste del recorrido de pila y desenredado es parecido al costo de una llamada de función. Estructuras de datos adicionales son necesarias para realizar el seguimiento de la pila de llamadas tras una `try` se entra en bloque e instrucciones adicionales son necesarias para desenredar la pila si se produce una excepción. Sin embargo, en la mayoría de los escenarios, el costo en rendimiento y consumo de memoria no es significativo. Los efectos adversos de excepciones en el rendimiento es probable que sea significativo únicamente en sistemas muy limitada de memoria o de rendimiento críticos bucles donde es probable que se producen con regularidad un error y el código para controlar estrechamente al código que lo notifica. En cualquier caso, es imposible conocer el costo real de excepciones sin la generación de perfiles y medición. Incluso en esos casos raros cuando el costo es importante, puede pesar, con la mayor exactitud, mantenimiento más fácil y otras ventajas proporcionadas por una directiva de excepción bien diseñada.  
  
## <a name="exceptions-vs-assertions"></a>Excepciones frente a aserciones  
 Excepciones y las aserciones son dos mecanismos diferentes para detectar errores en tiempo de ejecución en un programa. Utilice aserciones para probar condiciones durante el desarrollo que nunca debe ser true si todo el código es correcto. No hay ningún punto de control de este tipo de error con una excepción porque el error indica que algo en el código tiene que ser fijo y no representa una condición de que el programa debe recuperarse en tiempo de ejecución. Una aserción detiene la ejecución de la instrucción para que puede inspeccionar el estado del programa en el depurador; una excepción continúa la ejecución desde el primer controlador catch correspondiente. Usar excepciones para comprobar las condiciones de error que pueden producirse en tiempo de ejecución, incluso si el código es correcto, por ejemplo, "archivo no encontrado" o "memoria insuficiente." Puede recuperarse de estas condiciones, incluso si la recuperación sólo enviará un mensaje en un registro y finaliza el programa. Compruebe siempre los argumentos para funciones públicas mediante el uso de excepciones. Incluso si la función presenta errores, no tendrá control completo sobre los argumentos que un usuario puede pasar a él.  
  
## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Excepciones de C++ frente a excepciones SEH de Windows  
 Los programas de C y C++ pueden utilizar el mecanismo (SEH) en el sistema operativo Windows de control de excepciones estructurado. Los conceptos de SEH se parecen a las excepciones de C++, salvo que utiliza SEH el `__try`, `__except`, y `__finally` construye en lugar de `try` y `catch`. En Visual C++, las excepciones de C++ se implementan para SEH. Sin embargo, cuando se escribe código de C++, utilice la sintaxis de excepción de C++.  
  
 Para obtener más información acerca de SEH, consulte [control estructurado de excepciones (C/C ++)](../cpp/structured-exception-handling-c-cpp.md).  
  
## <a name="exception-specifications-and-noexcept"></a>Noexcept y especificaciones de excepciones  
 Especificaciones de excepciones se incluyeron en C++ como una manera de especificar las excepciones que puede producir una función. Sin embargo, las especificaciones de excepciones resultó problemáticas en la práctica y están desusadas en el estándar C ++ 11 borrador. Se recomienda que no usan las especificaciones de excepciones excepto `throw()`, que indica que la excepción no permite que escapen excepciones. Si debe utilizar las especificaciones de excepciones del tipo `throw(`*tipo*`)`, tenga en cuenta que [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] sale de estándar de ciertas maneras. Para obtener más información, consulte [especificaciones de excepciones (throw)](../cpp/exception-specifications-throw-cpp.md). El `noexcept` especificador se introdujo en C ++ 11 como la alternativa preferida para `throw()`.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: interfaz entre código excepcional y no excepcional](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)   
 [Bienvenido nuevamente a C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)