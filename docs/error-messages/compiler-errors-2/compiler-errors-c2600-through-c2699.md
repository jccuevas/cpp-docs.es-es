---
title: Errores del compilador de C2600 a C2699
ms.date: 04/21/2019
f1_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
helpviewer_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
ms.assetid: 73c6319f-cbea-4a2f-913b-90dc1af61f64
ms.openlocfilehash: 9ac5f5724490574aecf0e5b542f6fdd42b0ae5bb
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857056"
---
# <a name="compiler-errors-c2600-through-c2699"></a>Errores del compilador de C2600 a C2699

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C2600](compiler-error-c2600.md)|'*función*': no se puede definir una función miembro especial generada por el compilador (se debe declarar primero en la clase)|
|[Error del compilador C2601](compiler-error-c2601.md)|'*función*': las definiciones de función local no son válidas|
|[Error del compilador C2602](compiler-error-c2602.md)|'*clase*::*identificador*'no es un miembro de una clase base de'*clase*'|
|[Error del compilador C2603](compiler-error-c2603.md)|'*función*': Hay demasiados objetos static en ámbito de bloque con constructores/destructores en la función|
|Error del compilador C2604|'*identificador*': No se puede implementar más de un método de interfaz|
|[Error del compilador C2605](compiler-error-c2605.md)|'*identificador*': este método está reservado dentro de una clase administrada o WinRT|
|Error del compilador C2606|'*class1*': no se puede volver a implementar '*miembro*', tal y como se heredó de base de tiempo de ejecución'*class2*'|
|Error del compilador C2607|Error de aserción estática|
|Error del compilador C2608|Obsoleto.|
|Error del compilador C2609|Obsoleto.|
|Error del compilador C2610|'*clase*::*miembro*': no es una función miembro especial que puede ser su valor predeterminada|
|[Error del compilador C2611](compiler-error-c2611.md)|'*token*': elemento no válido después ' ~' (se esperaba un identificador)|
|[Error del compilador C2612](compiler-error-c2612.md)|finales '*carácter*' no válido en la lista de inicializadores de base o miembro|
|[Error del compilador C2613](compiler-error-c2613.md)|finales '*carácter*' no válido en la lista de clases base|
|[Error del compilador C2614](compiler-error-c2614.md)|'*clase*': inicialización de miembro no válido: '*identificador*' no es una base o miembro|
|Error del compilador C2615|Obsoleto.|
|[Error del compilador C2616](compiler-error-c2616.md)|'*conversión*': no se puede convertir implícitamente un valor que no sea l '*type1*' a un '*type2*' que no sea const|
|[Error del compilador C2617](compiler-error-c2617.md)|'*función*': instrucción return incoherente|
|Error del compilador C2618|Obsoleto.|
|[Error del compilador C2619](compiler-error-c2619.md)|'*identificador*': no se permite un miembro de datos estáticos en un struct/union anónimas|
|Error del compilador C2620|Obsoleto.|
|Error del compilador C2621|Obsoleto.|
|Error del compilador C2622|Obsoleto.|
|Error del compilador C2623|Obsoleto.|
|[Error del compilador C2624](compiler-error-c2624.md)|'*ámbito*::*tipo*': las clases locales no se puede usar para declarar variables 'extern'|
|Error del compilador C2625|'*identificador*': miembro union no válido; el tipo '*tipo*' es de tipo de referencia|
|[Error del compilador C2626](compiler-error-c2626.md)|'*identificador*': no se permite un miembro de datos privados y protegidos en un struct/union anónimas|
|[Error del compilador C2627](compiler-error-c2627.md)|'*función*': función miembro no permitida en unión anónima|
|[Error del compilador C2628](compiler-error-c2628.md)|'*type1*'seguido por'*type2*' no es válido (¿olvidó un ';'?)|
|Error del compilador C2629|'*identificador*': un struct/union anónimas no se puede declarar un tipo anidado|
|[Error del compilador C2630](compiler-error-c2630.md)|'*símbolo*' encontrado en lo que debe ser una lista separada por comas|
|Error del compilador C2631|'*identificador*': no se puede definir una clase o una enumeración en una plantilla de alias|
|[Error del compilador C2632](compiler-error-c2632.md)|'*type1*'seguido por'*type2*' no es válido|
|[Error del compilador C2633](compiler-error-c2633.md)|'*identificador*': 'inline' es la clase de almacenamiento válida sólo para los constructores|
|[Error del compilador C2634](compiler-error-c2634.md)|'*clase*::*miembro*': puntero a miembro de referencia no es válido|
|[Error del compilador C2635](compiler-error-c2635.md)|no se puede convertir un '*type1*\*' a un '*type2*\*'; se presupone la conversión de una clase base virtual|
|[Error del compilador C2636](compiler-error-c2636.md)|'*identificador*': puntero a miembro de referencia no es válido|
|[Error del compilador C2637](compiler-error-c2637.md)|'*identificador*': no se puede modificar los punteros a miembros de datos|
|[Error del compilador C2638](compiler-error-c2638.md)|'*identificador*': __based modificador no es válido para punteros a miembros|
|Error del compilador C2639|Obsoleto.|
|[Error del compilador C2640](compiler-error-c2640.md)|'*identificador*': __based no es válido modificador para referencia|
|Error del compilador C2641|Obsoleto.|
|Error del compilador C2642|Obsoleto.|
|Error del compilador C2643|Obsoleto.|
|Error del compilador C2644|Obsoleto.|
|[Error del compilador C2645](compiler-error-c2645.md)|ningún nombre completo para puntero a miembro (se encontró ':: *')|
|[Error del compilador C2646](compiler-error-c2646.md)|un struct/union anónimas en global o ámbito de espacio de nombres debe declararse como static|
|[Error del compilador C2647](compiler-error-c2647.md)|'*operador*': no se puede desreferenciar un '*type1*' en un '*type2*'|
|[Error del compilador C2648](compiler-error-c2648.md)|'*identificador*': uso de miembro como parámetro predeterminado requiere un miembro static|
|[Error del compilador C2649](compiler-error-c2649.md)|'*identificador*': no es 'class/struct/union'|
|[Error del compilador C2650](compiler-error-c2650.md)|'*operador*': no puede ser una función virtual|
|[Error del compilador C2651](compiler-error-c2651.md)|'*tipo*': operando izquierdo de '::' debe ser una clase, struct o union|
|[Error del compilador C2652](compiler-error-c2652.md)|'*identificador*': constructor de copias no válido: primer parámetro no debe ser un '*tipo*'|
|[Error del compilador C2653](compiler-error-c2653.md)|'*identificador*': no es un nombre de clase o espacio de nombres|
|[Error del compilador C2654](compiler-error-c2654.md)|'*identificador*': intento de acceso a un miembro fuera de una función miembro|
|[Error del compilador C2655](compiler-error-c2655.md)|'*identificador*': definición o nueva declaración no válida en el ámbito actual|
|[Error del compilador C2656](compiler-error-c2656.md)|'*función*': función no está permitida como un campo de bits|
|[Error del compilador C2657](compiler-error-c2657.md)|'*clase*:: *' se encuentra al principio de una instrucción (¿olvidó especificar un tipo?)|
|[Error del compilador C2658](compiler-error-c2658.md)|'*identificador*': nueva definición en struct/union anónimas|
|[Error del compilador C2659](compiler-error-c2659.md)|'*operador*': función como operando izquierdo|
|[Error del compilador C2660](compiler-error-c2660.md)|'*función*': función no acepta *número* argumentos|
|[Error del compilador C2661](compiler-error-c2661.md)|'*función*': ninguna función sobrecargada acepta *número* argumentos|
|[Error del compilador C2662](compiler-error-c2662.md)|'*función*': no se puede convertir el puntero 'this' de '*type1*'para'*type2*'|
|[Error del compilador C2663](compiler-error-c2663.md)|'*función*': *número* sobrecargas no tienen ninguna conversión válida para el puntero 'this'|
|[Error del compilador C2664](compiler-error-c2664.md)|'*función*': no se puede convertir el argumento *número* desde '*type1*'para'*type2*'|
|[Error del compilador C2665](compiler-error-c2665.md)|'*función*': ninguno de los *número* sobrecargas pudieran convertir todos los tipos de argumento|
|[Error del compilador C2666](compiler-error-c2666.md)|'*función*': *número* sobrecargas tienen conversiones similares|
|[Error del compilador C2667](compiler-error-c2667.md)|'*función*': ninguno de *número* sobrecargas tienen una conversión mejor|
|[Error del compilador C2668](compiler-error-c2668.md)|'*función*': llamada ambigua a una función sobrecargada|
|[Error del compilador C2669](compiler-error-c2669.md)|función miembro no permitida en unión anónima|
|[Error del compilador C2670](compiler-error-c2670.md)|'*función*': la plantilla de función no puede convertir el parámetro *número* de tipo '*tipo*'|
|[Error del compilador C2671](compiler-error-c2671.md)|'*función*': las funciones miembro static no tienen punteros 'this'|
|[Error del compilador C2672](compiler-error-c2672.md)|'*función*': no hay coincidencia sobrecargados se encuentra la función|
|[Error del compilador C2673](compiler-error-c2673.md)|'*función*': las funciones globales no tienen punteros 'this'|
|[Error del compilador C2674](compiler-error-c2674.md)|no se permite una declaración genérica en este contexto|
|[Error del compilador C2675](compiler-error-c2675.md)|unario '*operador*': '*tipo*' no define este operador o una conversión a un tipo aceptable para el operador predefinido|
|[Error del compilador C2676](compiler-error-c2676.md)|binario '*operador*': '*tipo*' no define este operador o una conversión a un tipo aceptable para el operador predefinido|
|[Error del compilador C2677](compiler-error-c2677.md)|binario '*operador*': encontró un ningún operador global que adopte el tipo '*tipo*' (o no hay ninguna conversión aceptable)|
|[Error del compilador C2678](compiler-error-c2678.md)|binario '*operador*': encontró ningún un operador que adopte un operando izquierdo de tipo '*tipo*' (o no hay ninguna conversión aceptable)|
|[Error del compilador C2679](compiler-error-c2679.md)|binario '*operador*': encontró ningún operador que adopte un operando derecho del tipo '*tipo*' (o no hay ninguna conversión aceptable)|
|[Error del compilador C2680](compiler-error-c2680.md)|'*tipo*': tipo de destino no válido para *cast*|
|[Error del compilador C2681](compiler-error-c2681.md)|'*tipo*': tipo de expresión no válida para *cast*|
|[Error del compilador C2682](compiler-error-c2682.md)|no se puede usar '*cast*' para convertir de'*type1*'para'*type2*'|
|[Error del compilador C2683](compiler-error-c2683.md)|'*cast*': '*tipo*' no es un tipo polimórfico|
|Error del compilador C2684|'*declarador*': no se admiten las funciones establecidas como valor predeterminadas y eliminadas en las clases administradas o WinRT|
|Error del compilador C2685|'*declarador*': no se admiten las funciones establecidas como valor predeterminadas y eliminadas con especificadores de restricción explícitos|
|Error del compilador C2686|no se pueden sobrecargar funciones miembro estáticas y no static con los mismos tipos de parámetro|
|[Error del compilador C2687](compiler-error-c2687.md)|'*tipo*': declaración de excepción no puede ser 'void' o denotar un tipo incompleto, puntero o referencia a un tipo incompleto|
|[Error del compilador C2688](compiler-error-c2688.md)|'*tipo*::*miembro*': con varios valores devueltos de covariante o herencia virtual no es compatible con funciones varargs|
|[Error del compilador C2689](compiler-error-c2689.md)|'*función*': no se puede definir una función friend en una clase local|
|[Error del compilador C2690](compiler-error-c2690.md)|'*operador*': no se puede realizar aritmética con punteros en una matriz administrada o WinRT|
|[Error del compilador el error C2691](compiler-error-c2691.md)|'*tipo*': una matriz administrada o WinRT no puede tener este tipo de elemento|
|[Error del compilador C2692](compiler-error-c2692.md)|'*función*': ajusten completamente al prototipo funciones requeridas en el compilador de C con el ' / clr' opción|
|[Error del compilador C2693](compiler-error-c2693.md)|'*operador*': comparación no válida de referencias a una matriz administrada o WinRT|
|[Error del compilador C2694](compiler-error-c2694.md)|'*función_de_reemplazo*': función virtual de invalidación tiene especificación de excepción menos restrictiva que la función miembro virtual de clase base '*función_base*'|
|[Error del compilador C2695](compiler-error-c2695.md)|'*función_de_reemplazo*': reemplazar la función virtual difiere de '*función_base*' sólo por convención de llamada|
|[Error del compilador C2696](compiler-error-c2696.md)|No se puede crear un objeto temporal de tipo administrado o WinRT '*tipo*'|
|Error del compilador C2697|Obsoleto.|
|[Error del compilador C2698](compiler-error-c2698.md)|la declaración using para '*declaration1*' no puede coexistir con la declaración using existente para'*declaration2*'|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
