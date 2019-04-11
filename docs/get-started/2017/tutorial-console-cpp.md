---
title: Creación de un proyecto de aplicación de consola de C++
description: Creación de una aplicación de consola Hola mundo y una aplicación de calculadora en Visual C++
ms.custom: mvc
ms.date: 03/25/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: b15bc7551c4bf99b6dd52f99bb5e69064ddb8308
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58867372"
---
# <a name="create-a-c-console-app-project"></a>Creación de un proyecto de aplicación de consola de C++

El punto de partida habitual para un programador de C++ es una aplicación "Hola mundo" que se ejecuta en la línea de comandos. Esto es lo que creará en Visual Studio en este artículo. Después, pasaremos a algo más complicado: una aplicación de calculadora.

## <a name="prerequisites"></a>Requisitos previos

- Instalar y ejecutar Visual Studio con la carga de trabajo **Desarrollo para el escritorio con C++** en el equipo. Si todavía no está instalada, vea [Instalar compatibilidad con C++ en Visual Studio](../../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Creación del proyecto de aplicación

Visual Studio usa *proyectos* para organizar el código de una aplicación y *soluciones* para organizar los proyectos. Un proyecto contiene todas las opciones, las configuraciones y las reglas que se usan para compilar las aplicaciones. También sirve para administrar la relación entre todos los archivos del proyecto y cualquier archivo externo. Para crear la aplicación, primero tendrá que crear un proyecto y una solución.

1. En la barra de menús de Visual Studio, seleccione **Archivo** > **Nuevo** > **Proyecto**. Se abrirá la ventana **Nuevo proyecto**.

2. En la barra lateral de la izquierda, asegúrese de que **Visual C++** está seleccionado. En el centro, haga clic en **Aplicación de consola de Windows**.

3. En el cuadro de edición **Nombre** de la parte inferior, asigne el nombre *CalculatorTutorial* al nuevo proyecto y, después, haga clic en **Aceptar**.

   ![Cuadro de diálogo Nuevo proyecto](./media/calculator-new-project-dialog.png "The New Project dialog")

   Se crea una aplicación de consola de Windows de C++ vacía. Las aplicaciones de consola usan una ventana de consola de Windows para mostrar la salida y aceptar la entrada del usuario. En Visual Studio, se abre una ventana del editor en la que se muestra el código generado:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n"; 
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started: 
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>Compruebe que la nueva aplicación se compila y ejecuta

La plantilla para una nueva aplicación de consola de Windows crea una sencilla aplicación "Hola mundo" de C++. En este momento, puede ver cómo Visual Studio compila y ejecuta las aplicaciones que crea directamente desde el IDE.

1. Para compilar el proyecto, seleccione **Compilar solución** en el menú **Compilar**. En la ventana **Salida** se muestran los resultados del proceso de compilación.

   ![Compilación del proyecto](./media/calculator-initial-build-output.png "Build the project")

1. Para ejecutar el código, en la barra de menús, seleccione **Depurar**, **Iniciar sin depurar**.

   ![Inicio del proyecto](./media/calculator-hello-world-console.png "Start the project")

   Se abre una ventana de consola y después se ejecuta la aplicación. Al iniciar una aplicación de consola en Visual Studio, ejecuta el código y después imprime "Presione cualquier tecla para continuar . " para ofrecerle la oportunidad de ver la salida. ¡Enhorabuena! Ha creado la primera aplicación de consola "Hola mundo" en Visual Studio.

1. Presione una tecla para cerrar la ventana de la consola y volver a Visual Studio.

Ahora tiene las herramientas para compilar y ejecutar la aplicación después de cada cambio, para comprobar que el código sigue funcionando según lo esperado. Más adelante, se mostrará cómo depurarlo si no funciona.

## <a name="edit-the-code"></a>Edición del código

Ahora, el código de esta plantilla se va a convertir en una aplicación de calculadora.

1. En el archivo *CalculatorTutorial.cpp*, modifique el código para que coincida con este ejemplo:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > Descripción del código:
   >
   > - Las instrucciones `#include` permiten hacer referencia a código que se encuentra en otros archivos. En ocasiones, es posible que vea un nombre de archivo incluido entre corchetes angulares (**\<\>**); en otras, está rodeado por comillas (**" "**). En general, los corchetes angulares se usan al hacer referencia a la biblioteca C++ Standard, mientras que las comillas se usan para otros archivos.
   > - La línea `#include "pch.h"` (o en versiones anteriores de Visual Studio, `#include "stdafx.h"`) hace referencia a algo que se conoce como un encabezado precompilado. Los programadores profesionales los suelen usar para mejorar los tiempos de compilación, pero están fuera del ámbito de este tutorial.
   > - La línea `using namespace std;` indica al compilador que espere que en este archivo se usen elementos de la biblioteca C++ Standard. Sin esta línea, cada palabra clave de la biblioteca tendría que ir precedida de `std::`, para denotar su ámbito. Por ejemplo, sin esa línea, cada referencia a `cout` se tendría que escribir como `std::cout`. La instrucción `using` se agrega para que el código parezca más limpio.
   > - La palabra clave `cout` se usa para imprimir en la salida estándar de C++. El operador **\<\<** indica al compilador que envíe a la salida estándar todo lo que esté a su derecha.
   > - La palabra clave **endl** es similar a la tecla Entrar; finaliza la línea y mueve el cursor a la siguiente. Un procedimiento recomendado consiste en colocar un elemento `\n` dentro de una cadena (entre "") para hacer lo mismo, ya que `endl` siempre vacía el búfer y puede afectar al rendimiento del programa, pero como esta aplicación es muy pequeña, en su lugar se usa `endl` para mejorar la legibilidad.
   > - Todas las instrucciones de C++ deben terminar en punto y coma, y todas las aplicaciones de C++ deben contener una función `main()`. Esta función es lo que el programa ejecuta al inicio. Todo el código debe ser accesible desde `main()` para que se pueda usar.

1. Para guardar el archivo, presione **Ctrl+S**, o bien haga clic en el icono **Guardar** situado cerca de la parte superior del IDE, el icono de disco de la barra de herramientas en la barra de menús.

1. Para ejecutar la aplicación, presione **Ctrl+F5**, o bien vaya al menú **Depurar** y seleccione **Iniciar sin depurar**. Si aparece el mensaje emergente **Este proyecto no está actualizado**, puede activar **No volver a mostrar este cuadro de diálogo** y, después, hacer clic en **Sí** para compilar la aplicación. Debería ver aparecer una ventana de consola que muestra el texto especificado en el código.

   ![Compilación e inicio de la aplicación](./media/calculator-first-launch.gif "Build and start your application")

1. Cuando haya terminado, cierre la ventana de la consola.

## <a name="add-code-to-do-some-math"></a>Adición de código para realizar cálculos matemáticos

Es el momento de agregar cierta lógica matemática.

### <a name="to-add-a-calculator-class"></a>Para agregar una clase Calculator

1. Vaya al menú **Proyecto** y seleccione **Agregar clase**. En el cuadro de edición **Nombre de clase**, escriba *Calculator*. Elija **Aceptar**. Se agregan dos nuevos archivos al proyecto. Para guardar todos los archivos modificados a la vez, presione **Ctrl+Mayús+S**. Se trata de un método abreviado de teclado para **Archivo** > **Guardar todo**. También hay un botón de la barra de herramientas para **Guardar todo**, un icono de dos discos, que se encuentra junto al botón **Guardar**. En general, se recomienda **Guardar todo** con frecuencia, para no perder ningún archivo al guardar.

   ![Creación de la clase Calculator](./media/calculator-create-class.gif "Create the Calculator class")

   Una clase es como un plano técnico para un objeto que realiza una acción. En este caso, se define una calculadora y cómo debería funcionar. El asistente **Agregar clase** que ha usado anteriormente ha creado archivos .h y .cpp con el mismo nombre que la clase. Puede ver una lista completa de los archivos del proyecto en la ventana **Explorador de soluciones** visible en el lateral del IDE. Si la ventana no es visible, puede abrirla desde la barra de menús: seleccione **Vista** > **Explorador de soluciones**.

   ![Explorador de soluciones](./media/calculator-solution-explorer.png "Explorador de soluciones")

   Ahora debería tener tres pestañas abiertas en el editor: *CalculatorTutorial.cpp*, *Calculator.h* y *Calculator.cpp*. Si cierra accidentalmente una de estas pestañas, puede volver a abrirla si hace doble clic en ella en la ventana **Explorador de soluciones**.

1. En **Calculator.h**, quite las líneas `Calculator();` y `~Calculator();` que se han generado, ya que aquí no serán necesarias. A continuación, agregue la línea de código siguiente para que el archivo tenga este aspecto:

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Descripción del código
   >
   > - En la línea que ha agregado se declara una función nueva llamada `Calculate`, que se usará para ejecutar las operaciones matemáticas de suma, resta, multiplicación y división.
   > - El código de C++ se organiza en archivos de *encabezado* (.h) y de *origen* (.cpp). Otros compiladores admiten otras extensiones de archivo, pero estas son las principales que debe conocer. Normalmente, las funciones y variables se *declaran*, es decir, se les asigna un nombre y un tipo, en los archivos de encabezado, y se *implementan* (se les asigna una definición) en los archivos de origen. Para acceder al código definido en otro archivo, puede usar `#include "filename.h"`, donde "filename.h" es el nombre del archivo que declara las variables o funciones que quiere usar.
   > - En las dos líneas que ha eliminado se declaraba un *constructor* y un *destructor* para la clase. Para una clase sencilla como esta, el compilador los crea de forma automática, y sus usos quedan fuera del ámbito de este tutorial.
   > - Es recomendable organizar el código en distintos archivos según lo que haga, para que después sea más sencillo encontrar el código que necesita. En este caso, la clase `Calculator` se define de forma independiente al archivo que contiene la función `main()`, pero el objetivo es hacer referencia a la clase `Calculator` en `main()`.

1. Aparecerá un subrayado ondulado de color verde debajo de `Calculate`. Esto se debe a que no se ha definido la función `Calculate` en el archivo .cpp. Mantenga el mouse sobre la palabra, haga clic en la bombilla que aparece y seleccione **Crear definición de "Calculate" en Calculator.cpp**. Aparecerá un mensaje emergente en el que se ofrece una vista del cambio de código que se ha realizado en el otro archivo. El código se ha agregado a *Calculator.cpp*.

   ![Creación de la definición de Calculate](./media/calculator-create-definition.gif "Create definition of Calculate")

   En la actualidad, solo devuelve 0,0. Vamos a cambiarlo. Presione **Esc** para cerrar la ventana emergente.

1. Cambie al archivo *Calculator.cpp* en la ventana del editor. Quite las secciones `Calculator()` y `~Calculator()` (como en el archivo .h) y agregue el código siguiente a `Calculate()`:

    ```cpp
    #include "pch.h"
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > Descripción del código
   >
   > - La función `Calculate` consume un número, un operador y un segundo número, y después realiza la operación solicitada en los números.
   > - La instrucción switch comprueba qué operador se ha proporcionado y solo ejecuta el caso correspondiente a esa operación. El valor predeterminado: case es una reserva en caso de que el usuario escriba un operador que no se acepta, para que el programa no se interrumpa. En general, se recomienda controlar la entrada no válida del usuario de una manera más elegante, pero esto queda fuera del ámbito de este tutorial.
   > - La palabra clave `double` denota un tipo de número que admite decimales. De este modo, la calculadora puede realizar operaciones matemáticas decimales y enteras. Es necesario que la función `Calculate` siempre devuelva un número como este debido a la presencia de `double` al principio del código (lo que denota el tipo de valor devuelto de la función), motivo por el que se devuelve 0,0 incluso en el caso predeterminado.
   > - En el archivo .h se declara el *prototipo* de la función, que indica al compilador por adelantado qué parámetros requiere y el tipo de valor devuelto que se puede esperar de ella. El archivo .cpp contiene todos los detalles de implementación de la función.

Si compila y ejecuta el código de nuevo en este momento, se cerrará después de preguntarle qué operación debe realizarse. A continuación, modificará la función `main` para realizar algunos cálculos.

### <a name="to-call-the-calculator-class-member-functions"></a>Para llamar a las funciones miembro de la clase Calculator

1. Ahora se va a actualizar la función `main` de *CalculatorTutorial.cpp*:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > Descripción del código
   >
   > - Como los programas de C++ siempre comienzan por la función `main()`, es necesario llamar al otro código desde ahí, por lo que se necesitará una instrucción `#include`.
   > - Se declaran varias variables iniciales (`x`, `y`, `oper` y `result`) para almacenar el primer número, el segundo, el operador y el resultado final, respectivamente. Siempre es aconsejable asignarles valores iniciales para evitar un comportamiento indefinido, que es lo que se hace aquí.
   > - En la línea `Calculator c;` se declara un objeto denominado "c" como una instancia de la clase `Calculator`. La propia clase es solo un plano técnico del funcionamiento de las calculadoras; el objeto es la calculadora concreta que realiza los cálculos matemáticos.
   > - La instrucción `while (true)` es un bucle. El código que contiene el bucle se sigue ejecutando repetidamente mientras la condición dentro de `()` sea true. Como la condición aparece simplemente como `true`, siempre es true, por lo que el bucle se ejecuta de forma indefinida. Para cerrar el programa, el usuario debe cerrar manualmente la ventana de la consola. En caso contrario, el programa siempre espera una entrada nueva.
   > - La palabra clave `cin` se usa para aceptar la entrada del usuario. Esta secuencia de entrada es lo suficientemente inteligente como para procesar una línea de texto especificado en la ventana de consola y colocarla dentro de cada una de las variables enumeradas, en orden, siempre que la entrada del usuario coincida con la especificación necesaria. Puede modificar esta línea para que acepte otros tipos de entrada, por ejemplo, más de dos números, aunque también se tendría que actualizar la función `Calculate()` para que lo procesara.
   > - La expresión `c.Calculate(x, oper, y);` llama a la función `Calculate` definida anteriormente y proporciona los valores de entrada especificados. Después, la función devuelve un número que se almacena en `result`.
   > - Por último, se imprime `result` en la consola, para que el usuario vea el resultado del cálculo.

### <a name="build-and-test-the-code-again"></a>Volver a compilar y probar el código

Ahora es el momento de volver a probar el programa para asegurarse de que todo funciona correctamente.

1. Presione **Ctrl+F5** para recompilar e iniciar la aplicación.

1. Escriba `5 + 5` y presione **Entrar**. Compruebe que el resultado es 10.

   ![El resultado de 5 + 5](./media/calculator-five-plus-five.png "The result of 5 + 5")

## <a name="debug-the-app"></a>Depurar la aplicación

Como el usuario tiene libertad para escribir lo que quiera en la ventana de la consola, nos aseguraremos de que la calculadora controla las entradas según lo previsto. En lugar de ejecutar el programa, se va a depurar, para poder inspeccionar con detalle lo que hace, paso a paso.

### <a name="to-run-the-app-in-the-debugger"></a>Para ejecutar la aplicación en el depurador

1. Establezca un punto de interrupción en la línea `result = c.Calculate(x, oper, y);`, justo después de que se haya solicitado la entrada al usuario. Para ello, haga clic en la línea en la barra vertical de color gris del borde izquierdo de la ventana del editor. Aparece un punto rojo.

   ![Establecimiento de un punto de interrupción](./media/calculator-set-breakpoint.gif "Set a breakpoint")

   Ahora, cuando se depure el programa, la ejecución siempre se detendrá en esa línea. Ya tenemos una idea aproximada de que el programa funciona para casos sencillos. Ya que no queremos pausar la ejecución cada vez, vamos a hacer condicional un punto de interrupción.

1. Haga clic con el botón derecho en el punto de color rojo que representa el punto de interrupción y seleccione **Condiciones**. En el cuadro de edición para la condición, escriba `(y == 0) && (oper == '/')`. Elija el botón **Cerrar** cuando haya terminado. La condición se guarda automáticamente.

   ![Establecimiento de un punto de interrupción condicional](./media/calculator-conditional-breakpoint.gif "Set a conditional breakpoint")

   Ahora, la ejecución se detiene en el punto de interrupción solo si se intenta realizar una división por 0.

1. Para depurar el programa, presione **F5** o haga clic en el botón de la barra de herramientas **Depurador local de Windows** con el icono de flecha de color verde. En la aplicación de consola, si escribe algo parecido a "5 - 0", el programa se comporta con normalidad y se sigue ejecutando. Pero si escribe "10 / 0", se detiene en el punto de interrupción. Incluso puede agregar cualquier número de espacios entre el operador y los números; `cin` es lo suficientemente inteligente como para analizar la entrada de forma adecuada.

   ![Pausa en el punto de interrupción condicional](./media/calculator-debug-conditional.gif "Pause at the conditional breakpoint")

### <a name="useful-windows-in-the-debugger"></a>Ventanas útiles del depurador

Cada vez que se depura el código, es posible que observe que aparecen ventanas nuevas. Estas ventanas pueden ayudar a la experiencia de depuración. Fíjese en la ventana **Automático**. En la ventana **Automático** se muestran los valores actuales de las variables que se han usado al menos tres líneas antes y hasta la línea actual.

   ![La ventana Automático](./media/calculator-autos.png "The Autos window")

Para ver todas las variables de esa función, cambie a la ventana **Variables locales**. En realidad puede modificar los valores de estas variables durante la depuración, para ver qué efecto tienen en el programa. En este caso, se dejarán como están.

   ![La ventana Variables locales](./media/calculator-locals.png "The Locals window")

También puede mantener el puntero sobre las variables en el propio código para ver sus valores actuales en donde se detiene la ejecución. Para asegurarse de que la ventana del editor tiene el foco, haga clic en ella primero.

   ![Mantenimiento del cursor para ver los valores de variable actuales](./media/calculator-hover-tooltip.gif "Hover to view current variable values")

### <a name="to-continue-debugging"></a>Para continuar la depuración

1. En la línea de color amarillo de la izquierda se muestra el punto de ejecución actual. La línea actual llama a `Calculate`, por lo que presione **F11** para **Depurar paso a paso por instrucciones** la función. Se encontrará en el cuerpo de la función `Calculate`. Tenga cuidado con **Depurar paso a paso por instrucciones**; si lo ejecuta demasiado, puede perder mucho tiempo. Pasa por cualquier código que se utilice en la línea en la que se encuentre, incluidas las funciones de biblioteca estándar.

1. Ahora que el punto de ejecución está al principio de la función `Calculate`, presione **F10** para pasar a la línea siguiente en la ejecución del programa. **F10** también se conoce como **Depurar paso a paso por procedimientos**. Se puede usar **Depurar paso a paso por procedimientos** para pasar de una línea a otra, sin profundizar en los detalles de lo que ocurre en cada elemento de la línea. En general, se debe usar **Depurar paso a paso por procedimientos** en lugar de **Depurar paso a paso por instrucciones**, a menos que quiera profundizar más en el código que se llama desde otra parte (como hizo para llegar al cuerpo de `Calculate`).

1. Siga presionando **F10** para **Depurar paso a paso por procedimientos** cada línea hasta que regrese a la función `main()` del otro archivo, y deténgase en la línea `cout`.

   ![Depuración paso a paso por procedimientos de Calculate y comprobación del resultado](./media/calculator-undefined-zero.gif "Step out of Calculate and check result")

   Parece que el programa hace lo que se espera: toma el primer número y lo divide por el segundo. En la línea `cout`, mantenga el puntero sobre la variable `result` o examine `result` en la ventana **Automático**. Verá que su valor se muestra como "inf", que no se ve bien, así que vamos a arreglarlo. En la línea `cout` solo se muestra el valor almacenado en `result`, por lo que al avanzar una línea más mediante **F10**, en la ventana de consola se muestra:

   ![El resultado de la división por cero](./media/calculator-divide-by-zero-fail.png "The result of divide by zero")

   Este resultado sucede porque la división por cero no está definida, por lo que el programa no tiene una respuesta numérica a la operación solicitada.

### <a name="to-fix-the-divide-by-zero-error"></a>Para corregir el error de "división por cero"

Vamos a controlar la división por cero de forma más elegante, para que un usuario pueda entender el problema.

1. Realice los cambios siguientes en *CalculatorTutorial.cpp*. (Puede dejar el programa en ejecución mientras realiza los cambios, gracias a una característica del depurador denominada **Editar y continuar**):

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. Ahora presione **F5** una vez. La ejecución del programa continúa hasta que tiene que detenerse para solicitar la entrada del usuario. Vuelva a escribir `10 / 0`. Ahora, se imprime un mensaje más útil. Al usuario se le solicita una entrada adicional y el programa se continúa ejecutando con normalidad.

   ![El resultado final después de realizar los cambios](./media/calculator-final-verification.gif "The final result after changes")

   > [!Note]
   > Cuando se edita código en modo de depuración, hay riesgo de que se vuelva obsoleto. Esto sucede cuando el depurador sigue ejecutando el código antiguo y todavía no se ha actualizado con los cambios. El depurador abre un cuadro de diálogo en el que se le informará cuando esto ocurra. En ocasiones, es posible que deba presionar **F5** para actualizar el código que se está ejecutando. En concreto, si realiza un cambio dentro de una función mientras el punto de ejecución está dentro de ella, tendrá que depurarla paso a paso por procedimientos y después volver a acceder a la función para obtener el código actualizado. Si por algún motivo eso no funciona y ve un mensaje de error, puede detener la depuración si hace clic en el cuadrado de color rojo de la barra de herramientas situada bajo los menús de la parte superior del IDE y después presionar **F5** o hacer clic en la flecha "Reproducir" de color verde situada junto al botón de detención en la barra de herramientas para volver a iniciar la depuración.
   
   > Descripción de los métodos abreviados de Ejecutar y Depurar
   >
   > - Mediante **F5** (o **Depurar** > **Iniciar depuración**) se inicia una sesión de depuración si todavía no hay ninguna activa, y se ejecuta el programa hasta que se alcanza un punto de interrupción o el programa necesita la entrada del usuario. Si no se necesita la entrada del usuario y no hay ningún punto de interrupción disponible, el programa finaliza y la ventana de la consola se cierra de forma automática cuando el programa termina de ejecutarse. Si tiene algo parecido a un programa "Hola mundo" para ejecutar, presione **Ctrl+F5** o establezca un punto de interrupción antes de presionar **F5** para mantener abierta la ventana.
   > - Mediante **Ctrl+F5** (o **Depurar** > **Iniciar sin depurar**) se ejecuta la aplicación sin entrar en modo de depuración. Esto es ligeramente más rápido que la depuración y la ventana de la consola permanece abierta después de que el programa termine de ejecutarse.
   > - **F10** (conocido como **Depurar paso a paso por procedimientos**) permite iterar por el código línea a línea y visualizar cómo se ejecuta y cuáles son los valores de variable en cada paso de la ejecución.
   > - **F11** (conocido como **Depurar paso a paso por instrucciones**) funciona de forma similar a **Depurar paso a paso por procedimientos**, con la excepción de que depura paso a paso por procedimientos las funciones a las que se llama en la línea de ejecución. Por ejemplo, si la línea que se está ejecutando llama a una función, al presionar **F11** el puntero se desplaza al cuerpo de la función, para que pueda seguir la ejecución del código de la función antes de volver a la línea de partida. Al presionar **F10** la llamada de función se depura paso a paso por instrucciones y simplemente pasa a la línea siguiente; la llamada de función se sigue produciendo, pero el programa no se detiene para mostrarle lo que está haciendo.

### <a name="close-the-app"></a>Cierre la aplicación

1. Si sigue en ejecución, cierre la ventana de la consola de la aplicación de calculadora.

## <a name="the-finished-app"></a>La aplicación finalizada

¡Enhorabuena! Ha completado el código de la aplicación de calculadora y lo ha compilado y depurado en Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

[Más información sobre Visual Studio para C++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)
