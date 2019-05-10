---
title: Errores del compilador de C2500 a C2599
ms.date: 04/21/2019
f1_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
helpviewer_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
ms.openlocfilehash: 87728c2d7055715b7e7d986d5ab8792ceba5c450
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857076"
---
# <a name="compiler-errors-c2500-through-c2599"></a>Errores del compilador de C2500 a C2599

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C2500](compiler-error-C2500.md)|'*identificador1*': '*identificador2*' ya es una clase base directa|
|Error del compilador C2501|'*identificador*': ' __declspec (*especificador*)' solo se puede aplicar a structs, uniones, clases o miembros de campo de bits sin signo|
|[Error del compilador C2502](compiler-error-C2502.md)|'*identificador*': hay demasiados modificadores de acceso en la clase base|
|[Error del compilador C2503](compiler-error-C2503.md)|'*clase*': las clases base no pueden contener matrices de tamaño cero|
|[Error del compilador C2504](compiler-error-C2504.md)|'*clase*': clase base sin definir|
|[Error del compilador C2505](compiler-error-C2505.md)|'*símbolo*': ' __declspec (*especificador*)' solo se puede aplicar a declaraciones o definiciones de objetos globales o miembros de datos estáticos|
|[Error del compilador C2506](compiler-error-C2506.md)|'*miembro*': ' __declspec (*especificador*)' no se puede aplicar a este símbolo|
|[Error del compilador C2507](compiler-error-C2507.md)|'*identificador*': hay demasiados modificadores virtuales en la clase base|
|Error del compilador C2508|'*identificador*': ' __declspec (*specifier1*)' no se puede combinar con ' __declspec (*specifier2*)'|
|[Error del compilador C2509](compiler-error-C2509.md)|'*identificador*': función miembro no declarada en '*clase*'|
|[Error del compilador C2510](compiler-error-C2510.md)|'*identificador*': operando izquierdo de '::' debe ser class/struct/union|
|[Error del compilador C2511](compiler-error-C2511.md)|'*identificador*': sobrecargar la función miembro no se encuentra en '*clase*'|
|[Error del compilador C2512](compiler-error-C2512.md)|'*identificador*': no hay disponible un constructor predeterminado adecuado|
|[Error del compilador C2513](compiler-error-C2513.md)|' * tipo ': ninguna variable declarada antes de '='|
|[Error del compilador C2514](compiler-error-C2514.md)|'*clase*': clase no tiene constructores|
|Error del compilador C2515|'*identificador*': 'vtguard' solamente se puede aplicar a definiciones o declaraciones de clase|
|[Error del compilador C2516](compiler-error-C2516.md)|'*clase*': no es una clase base válida|
|[Error del compilador C2517](compiler-error-C2517.md)|'*identificador*': derecho de '::' no está definido|
|[Error del compilador C2518](compiler-error-C2518.md)|palabra clave '*palabra clave*' no válido en la lista de clases base; se ha omitido|
|Error del compilador C2519|'*identificador*': Atributos de WinRT solo pueden contener campos públicos|
|Error del compilador C2520|'*clase*': no hay constructor no explícita disponible para la conversión implícita|
|[Error del compilador C2521](compiler-error-C2521.md)|un destructor/finalizador no toma ningún argumento|
|Error del compilador C2522|'*identificador*': No se puede utilizar el identificador de sobrecarga en '*identificador1*'como ya se especifica en'*identificador2*'|
|[Error del compilador C2523](compiler-error-C2523.md)|'*clase*:: ~*identificador*': error de coincidencia de etiqueta de destructor/finalizador|
|[Error del compilador C2524](compiler-error-C2524.md)|'*identificador*': un destructor/finalizador debe tener una lista de parámetros 'void'|
|Error del compilador C2525|'*identificador*': El parámetro '*identificador1*'denominado'*identificador2*' en la base de función y debe coincidir en una implementación publicada|
|[Error del compilador C2526](compiler-error-C2526.md)|'*identificador1*': Función de vinculación de C no puede devolver C++ clase*identificador2*'|
|Error del compilador C2527|'*identificador*': No se puede especificar defaultOverload en ambos '*función1*'y'*función2*'. Quite una especificación o cambie el nombre de la función durante la implementación|
|[Error del compilador C2528](compiler-error-C2528.md)|'*identificador*': puntero a referencia no es válido|
|[Error del compilador C2529](compiler-error-C2529.md)|'*identificador*': referencia a la referencia no es válido|
|[Error del compilador C2530](compiler-error-C2530.md)|'*identificador*': se deben inicializar referencias|
|[Error del compilador C2531](compiler-error-C2531.md)|'*identificador*': referencia de un campo no válida a bits|
|[Error del compilador C2532](compiler-error-C2532.md)|'*identificador*': modificador para referencia no válido|
|[Error del compilador C2533](compiler-error-C2533.md)|'*identificador*': los constructores no permitidos un tipo de valor devuelto|
|[Error del compilador C2534](compiler-error-C2534.md)|'*identificador*': constructor no puede devolver un valor|
|[Error del compilador C2535](compiler-error-C2535.md)|'*identificador*': función miembro ya definida o declarada|
|Error del compilador C2536|Obsoleto.|
|[Error del compilador C2537](compiler-error-C2537.md)|'*especificador*': especificación de vinculación no válida|
|Error del compilador C2538|Obsoleto.|
|Error del compilador C2539|Obsoleto.|
|[Error del compilador C2540](compiler-error-C2540.md)|expresión no constante como límite de matriz|
|[Error del compilador C2541](compiler-error-C2541.md)|'*identificador*': no se puede eliminar los objetos que no sean punteros|
|[Error del compilador C2542](compiler-error-C2542.md)|'*identificador*': el objeto de clase no tiene ningún constructor para la inicialización|
|[Error del compilador C2543](compiler-error-C2543.md)|se esperaba ']' para el operador '[']|
|[Error del compilador C2544](compiler-error-C2544.md)|se esperaba ')' para el operador '()'|
|[Error del compilador C2545](compiler-error-C2545.md)|'*operador*': no se puede encontrar el operador sobrecargado|
|Error del compilador C2546|'*identificador*': cuando se define un tipo en un PIA y no primario, debe hacer referencia a los PIA en primer lugar|
|Error del compilador C2547|'*identificador*': Todos los parámetros de un método publicado se deben designar explícitamente en la declaración|
|[Error del compilador C2548](compiler-error-C2548.md)|'*función*': falta el parámetro predeterminado para el parámetro *parámetro*|
|[Error del compilador C2549](compiler-error-C2549.md)|conversión definida por el usuario no puede especificar un tipo de valor devuelto|
|[Error del compilador C2550](compiler-error-C2550.md)|'*identificador*': las listas de inicializadores de constructor sólo se permiten en las definiciones de constructor|
|[Error del compilador C2551](compiler-error-C2551.md)|El tipo 'void *' necesita conversión explícita|
|[Error del compilador C2552](compiler-error-C2552.md)|'*identificador*': no agregados no se puede inicializar con una lista de inicializadores|
|[Error del compilador C2553](compiler-error-C2553.md)|'*tipo* *derived_class*::*función*': reemplazar el tipo de valor devuelto de función virtual difiere de '*tipo* *base_ clase*::*función*'|
|[Error del compilador C2555](compiler-error-C2555.md)|'*derived_class*::*función*': función virtual de invalidación tipo devuelto es diferente y no es covariante de '*$base_class*::*función*'|
|[Error del compilador C2556](compiler-error-C2556.md)|'*type1* *clase*::*función*': función sobrecargada solo se diferencie por tipo de valor devuelto de '*type2* *clase*::*función*'|
|[Error del compilador C2557](compiler-error-C2557.md)|'*identificador*': los miembros privados y protegidos no se puede inicializar sin un constructor|
|[Error del compilador C2558](compiler-error-C2558.md)|la clase*clase*': ningún constructor de copias disponible o el constructor de copias se declara 'explicit'|
|Error del compilador C2559|'*identificador*': no se pueden sobrecargar una función miembro sin el calificador de referencia con una función miembro con el calificador de referencia|
|Error del compilador C2560|'*identificador*': no se pueden sobrecargar una función miembro con el calificador de referencia con una función miembro sin el calificador de referencia|
|[Error del compilador C2561](compiler-error-C2561.md)|'*función*': función debe devolver un valor|
|[Error del compilador C2562](compiler-error-C2562.md)|'*función*': función 'void' que devuelve un valor|
|[Error del compilador C2563](compiler-error-C2563.md)|Error de coincidencia en la lista de parámetros formales|
|Error del compilador C2564|Obsoleto.|
|Error del compilador C2565|'*identificador*': calificador de referencia no es válido para constructores/destructores|
|[Error del compilador C2566](compiler-error-C2566.md)|función sobrecargada en expresión condicional|
|[Error del compilador C2567](compiler-error-C2567.md)|no se puede abrir los metadatos de '*filename*', *possible_reason*|
|[Error del compilador C2568](compiler-error-C2568.md)|'*identificador*': no se puede resolver la sobrecarga de función|
|[Error del compilador C2569](compiler-error-C2569.md)|'*identificador*': enum/union no se puede usar como clase base|
|[Error del compilador C2570](compiler-error-C2570.md)|'*identificador*': union no puede tener clases base|
|[Error del compilador C2571](compiler-error-C2571.md)|'*identificador*': función virtual no puede estar en la unión '*unión*'|
|[Error del compilador C2572](compiler-error-C2572.md)|'*función*': nueva definición del argumento predeterminado: parámetro *número*|
|[Error del compilador C2573](compiler-error-C2573.md)|'*clase*': no se pueden eliminar punteros a objetos de este tipo; la clase no tiene ninguna sobrecarga no ubicada para 'operator delete'. Use:: eliminar o agregar 'operador delete(void*)' a la clase|
|[Error del compilador C2574](compiler-error-C2574.md)|'*destructor*': no se puede declarar como static|
|[Error del compilador C2575](compiler-error-C2575.md)|'*identificador*': sólo las funciones miembro y las bases pueden ser virtuales|
|Error del compilador C2576|'*identificador*': no se puede introducir un nuevo método virtual como 'public'. Considere la posibilidad de hacer que el método no virtual o cambiar la accesibilidad a 'internal' o 'protected private'|
|[Error del compilador C2577](compiler-error-C2577.md)|'*identificador*': un destructor/finalizador no puede tener un tipo de valor devuelto|
|Error del compilador C2578|'*clase*': tipo no puede tener un constructor de 'protected public' o 'protected'|
|[Error del compilador C2579](compiler-error-C2579.md)|no se puede resolver el tipo *tipo* (*desplazamiento*). Se espera en *nombre de archivo*|
|Error del compilador C2580|'*identificador*': no se permiten varias versiones de un funciones miembro especiales establecidas como valor predeterminado|
|[Error del compilador C2581](compiler-error-C2581.md)|'*tipo*': estático ' operador =' no es válida (función)|
|[Error del compilador C2582](compiler-error-C2582.md)|' operador *operador*'función no está disponible en'*tipo*'|
|[Error del compilador C2583](compiler-error-C2583.md)|'*identificador*': ' const/volatile' puntero 'this' no es válido para constructores/destructores|
|[Error del compilador C2584](compiler-error-C2584.md)|'*clase*': base directa '*base_class2*' no está accesible; ya existe una base de '*base_class1*'|
|[Error del compilador C2585](compiler-error-C2585.md)|conversión explícita a '*tipo*' es ambiguo|
|[Error del compilador C2586](compiler-error-C2586.md)|sintaxis de conversión definido por el usuario incorrecta: direccionamientos indirectos no válidos|
|[Error del compilador C2587](compiler-error-C2587.md)|'*identificador*': uso no válido de variable local como parámetro predeterminado|
|[Error del compilador C2588](compiler-error-C2588.md)|':: ~*identificador*': no válido global destructor/finalizador|
|[Error del compilador C2589](compiler-error-C2589.md)|'*identificador*': símbolo (token) en el lado derecho de '::'|
|Error del compilador C2590|'*identificador*': solo un constructor puede tener una lista de inicializadores de base o miembro|
|Error del compilador C2591|ExclusiveTo no puede usar '*tipo*' como argumento. Solo 'ref class' es un argumento válido|
|[Error del compilador C2592](compiler-error-C2592.md)|'*clase*': '*base_class2*'se hereda de'*base_class1*' y no se pueden volver a especificar|
|[Error del compilador C2593](compiler-error-C2593.md)|' operador *identificador*' es ambiguo|
|[Error del compilador C2594](compiler-error-C2594.md)|'*operador*': conversiones ambiguas de '*type1*'para'*type2*'|
|Error del compilador C2595|'*identificador*' WinRT de un tipo de atributo debe ser sealed|
|Error del compilador C2596|'*identificador*' WinRT de un campo de atributo solo puede ser un 'public enum class', 'int', 'unsigned int', 'bool', 'Platform:: Type', 'Platform:: String' o 'Windows:: Foundation:: HResult'|
|[Error del compilador C2597](compiler-error-C2597.md)|referencia no válida a miembro no estático '*identificador*'|
|[Error del compilador C2598](compiler-error-C2598.md)|especificación de vinculación debe estar en el ámbito global|
|[Error del compilador C2599](compiler-error-C2599.md)|'*identificador*': no se permite la declaración adelantada de una enumeración administrada o WinRT|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
