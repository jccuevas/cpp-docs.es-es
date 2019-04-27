---
title: Errores del compilador de C2700 a C2799
ms.date: 04/21/2019
f1_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
helpviewer_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
ms.openlocfilehash: a6f4391008bf9b0a066ba65f27a41697c6097c2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153218"
---
# <a name="compiler-errors-c2700-through-c2799"></a>Errores del compilador de C2700 a C2799

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C2700](compiler-error-c2700.md)|'*tipo*': no se puede iniciar (utilice/W4 para obtener más información)|
|[Error del compilador C2701](compiler-error-c2701.md)|'*función*': una plantilla de función/genérica no puede ser un elemento friend de una clase local|
|[Error del compilador C2702](compiler-error-c2702.md)| __except no puede aparecer en el bloque de finalización|
|[Error del compilador C2703](compiler-error-c2703.md)|instrucción __leave no válida|
|[Error del compilador C2704](compiler-error-c2704.md)|'*función*': __va_start intrínseco solo se permite en varargs|
|[Error del compilador C2705](compiler-error-c2705.md)|'*etiqueta*': salto no válido en '*exception_block*' ámbito|
|[Error del compilador C2706](compiler-error-c2706.md)|__except no válido sin el correspondiente __try (falta '}' en el bloque __try?)|
|[Error del compilador C2707](compiler-error-c2707.md)|'*identificador*': contexto incorrecto para la función intrínseca|
|[Error del compilador C2708](compiler-error-c2708.md)|'*identificador*': la longitud de parámetros reales en bytes difiere de la llamada anterior o referencia|
|[Error del compilador C2709](compiler-error-c2709.md)|'*identificador*': la longitud de parámetros formales en bytes es diferente de la declaración anterior|
|[Error del compilador C2710](compiler-error-c2710.md)|'*identificador*': ' __declspec (*modificador*)' solo puede aplicarse a una función que devuelve un puntero|
|[Error del compilador C2711](compiler-error-c2711.md)|'*función*': esta función no se puede compilar como administrada, considere la posibilidad de usar #pragma no administrado|
|[Error del compilador C2712](compiler-error-c2712.md)|No se puede utilizar __try en funciones que requieren desenredo de objetos|
|[Error del compilador C2713](compiler-error-c2713.md)|permite solo una forma de control de excepciones por función|
|[Error del compilador C2714](compiler-error-c2714.md)|no se permite alignof (void)|
|[Error del compilador C2715](compiler-error-c2715.md)|'*tipo*': no se puede producir o detectar este tipo|
|Error del compilador C2716|Obsoleto.|
|Error del compilador C2717|Obsoleto.|
|[Error del compilador C2718](compiler-error-c2718.md)|'*tipo*': el parámetro real con alineación solicitada de *número* no se alineará|
|[Error del compilador C2719](compiler-error-c2719.md)|'*parámetro*': parámetro formal con alineación solicitada de *número* no se alineará|
|[Error del compilador C2720](compiler-error-c2720.md)|'*identificador*': '*especificador*' especificador de clase de almacenamiento no es válido para miembros|
|[Error del compilador C2721](compiler-error-c2721.md)|'*especificador*': especificador de clase de almacenamiento no es válido entre la palabra clave operator y el tipo|
|[Error del compilador C2722](compiler-error-c2722.md)|'::*operador*': comando no válido de operador siguiente; utilice ' operador *operador*'|
|[Error del compilador C2723](compiler-error-c2723.md)|'*función*': '*especificador*' especificador no es válido en la definición de función|
|[Error del compilador C2724](compiler-error-c2724.md)|'*función*': 'static' no debe usarse en funciones miembro definidas en el ámbito de archivo|
|[Error del compilador C2725](compiler-error-c2725.md)|'*tipo*': no se puede producir o detectar un objeto administrado o WinRT por valor o referencia|
|[Error del compilador C2726](compiler-error-c2726.md)|'gcnew' solo puede usarse para crear un objeto con tipo WinRT o administrado|
|Error del compilador C2727:|Obsoleto.|
|[Error del compilador C2728](compiler-error-c2728.md)|'*tipo*': una matriz nativa no puede contener este tipo|
|Error del compilador C2729|Obsoleto.|
|[Error del compilador C2730](compiler-error-c2730.md)|'*clase*': no puede ser una clase base de sí mismo|
|[Error del compilador C2731](compiler-error-c2731.md)|'*función*': no se puede sobrecargar la función|
|[Error del compilador C2732](compiler-error-c2732.md)|especificación de vinculación se contradice con la especificación anterior para '*función*'|
|[Error del compilador C2733](compiler-error-c2733.md)|'*función*': una segunda vinculación C de la función sobrecargada no permitida|
|[Error del compilador C2734](compiler-error-c2734.md)|'*identificador*': objeto 'const' debe inicializarse si no 'extern'|
|[Error del compilador C2735](compiler-error-c2735.md)|'*palabra clave*' no se permite la palabra clave en el especificador de tipo de parámetros formales|
|[Error del compilador C2736](compiler-error-c2736.md)|'*palabra clave*' no se permite la palabra clave en la conversión|
|Error del compilador C2737|'*identificador*': se debe inicializar el objeto 'constexpr'|
|[Error del compilador C2738](compiler-error-c2738.md)|' operador *tipo*': es ambiguo o no es un miembro de '*clase*'|
|[Error del compilador C2739](compiler-error-c2739.md)|'*número*': las dimensiones de matriz administrada o WinRT explícita deben estar entre 1 y 32|
|Error del compilador C2740|valor del operando '*número*'está fuera del intervalo'*lower_bound* - *upper_bound*'|
|Error del compilador C2741|tamaño de trama demasiado grande|
|Error del compilador C2742|Obsoleto.|
|[Error del compilador C2743](compiler-error-c2743.md)|'*tipo*': no se puede detectar un tipo nativo con el destructor __clrcall o el constructor de copias|
|Error del compilador C2744|'*operador*' no es un operador CLR o WinRT válido|
|[Error del compilador C2745](compiler-error-c2745.md)|'*token*': no se puede convertir este token para un identificador|
|Error del compilador C2746|Obsoleto.|
|Error del compilador C2747|Obsoleto.|
|[Error del compilador C2748](compiler-error-c2748.md)|creación de una matriz administrada o WinRT debe tener el tamaño de matriz o un inicializador de matriz|
|[Error del compilador C2749](compiler-error-c2749.md)|'*tipo*': solamente puede producir o detectar el identificador a una clase administrada con/CLR: safe|
|[Error del compilador C2750](compiler-error-c2750.md)|'*tipo*': no se puede utilizar 'new' en la referencia de tipo; Utilice 'gcnew' en su lugar|
|[Error del compilador C2751](compiler-error-c2751.md)|'*parámetro*': no se puede calificar el nombre de un parámetro de función|
|[Error del compilador C2752](compiler-error-c2752.md)|'*plantilla*': más de una especialización parcial coincide con la lista de argumentos de plantilla|
|[Error del compilador C2753](compiler-error-c2753.md)|'*plantilla*': la especialización parcial no puede coincidir con la lista de argumentos de plantilla principal|
|[Error del compilador C2754](compiler-error-c2754.md)|'*plantilla*': una especialización parcial no puede tener un parámetro de plantilla sin tipo dependiente|
|[Error del compilador C2755](compiler-error-c2755.md)|'*parámetro*': parámetro sin tipo de una especialización parcial debe ser un identificador simple|
|[Error del compilador C2756](compiler-error-c2756.md)|'*plantilla*': no se permite en una especialización parcial de argumentos de plantilla predeterminados|
|[Error del compilador C2757](compiler-error-c2757.md)|'*identificador*': ya existe un símbolo con este nombre y, por tanto, no se puede usar este nombre como un espacio de nombres|
|[Error del compilador C2758](compiler-error-c2758.md)|'*miembro*': debe inicializarse un miembro de tipo de referencia|
|Error del compilador C2759|informes de ensamblado en línea: *error_message*|
|[Error del compilador C2760](compiler-error-c2760.md)|error de sintaxis: se esperaba '*token1*'not'*token2*'|
|[Error del compilador C2761](compiler-error-c2761.md)|'*función*': nueva declaración de función miembro no permitida|
|[Error del compilador C2762](compiler-error-c2762.md)|'*plantilla*': expresión no válida como argumento de plantilla para '*parámetro*'|
|Error del compilador C2763|'*plantilla*': uso no válido de un literal de cadena como argumento de plantilla para '*parámetro*'|
|[Error del compilador C2764](compiler-error-c2764.md)|'*parámetro*': parámetro de plantilla no utilizado o deducible en la especialización parcial '*especialización*'|
|[Error del compilador C2765](compiler-error-c2765.md)|'*función*': una especialización explícita de una plantilla de función no puede tener ningún argumento predeterminado|
|[Error del compilador C2766](compiler-error-c2766.md)|especialización explícita; '*especialización*' ya se ha definido.|
|[Error del compilador C2767](compiler-error-c2767.md)|Error de coincidencia de dimensión de matriz administrada o WinRT: se esperaba *número* argumentos n - *número* proporcionado|
|[Error del compilador C2768](compiler-error-c2768.md)|'*función*': uso no válido de argumentos de plantilla explícitos|
|Error del compilador C2769|no puede inicializar de llave de una matriz administrada o WinRT en una lista de inicializadores de base o miembro|
|[Error del compilador C2770](compiler-error-c2770.md)|argumentos de plantilla o genérica explícita no válido para '*plantilla*'|
|[Error del compilador C2771](compiler-error-c2771.md)|#import solo se permite en un ámbito global o de espacio de nombres|
|Error del compilador C2772|Obsoleto.|
|[Error del compilador C2773](compiler-error-c2773.md)|#import y #using disponible solo en el compilador de C++|
|[Error del compilador C2774](compiler-error-c2774.md)|'*identificador*': no hay ningún método 'put' está asociado con esta propiedad|
|[Error del compilador C2775](compiler-error-c2775.md)|'*identificador*': no hay ningún método 'get' está asociado con esta propiedad|
|[Error del compilador C2776](compiler-error-c2776.md)|se puede especificar solo un método 'get' por propiedad|
|[Error del compilador C2777](compiler-error-c2777.md)|se puede especificar solo un método 'put' por propiedad|
|[Error del compilador C2778](compiler-error-c2778.md)|GUID formado incorrectamente en __declspec(uuid())|
|[Error del compilador C2779](compiler-error-c2779.md)|'*declaración*': los métodos de propiedad solo pueden asociarse con los miembros de datos no estáticos|
|[Error del compilador C2780](compiler-error-c2780.md)|'*declaración*': espera *número* argumentos - *número* proporcionado|
|[Error del compilador C2781](compiler-error-c2781.md)|'*declaración*': espera al menos *número* argumento - *número* proporcionado|
|[Error del compilador C2782](compiler-error-c2782.md)|'*declaración*': parámetro de plantilla o genérico '*parámetro*' es ambiguo|
|[Error del compilador C2783](compiler-error-c2783.md)|'*declaración*': no se pudo deducir el argumento de plantilla o genérico para '*identificador*'|
|[Error del compilador C2784](compiler-error-c2784.md)|'*declaración*': no se pudo deducir el argumento de plantilla o genérico para '*type1*'from'*type2*'|
|[Error del compilador C2785](compiler-error-c2785.md)|'*declaration1*'y'*declaration2*' tienen distintos tipos de valor devueltos|
|[Error del compilador C2786](compiler-error-c2786.md)|'*tipo*': operando no válido para __uuidof|
|[Error del compilador C2787](compiler-error-c2787.md)|'*identificador*': se ha asociado al objeto ningún GUID|
|[Error del compilador C2788](compiler-error-c2788.md)|'*identificador*': más de un GUID asociado a este objeto|
|Error del compilador C2789|'*identificador*': debe inicializarse un objeto de tipo calificado constante|
|[Error del compilador C2790](compiler-error-c2790.md)|'super': esta palabra clave solo puede usarse dentro del cuerpo de función miembro de clase|
|[Error del compilador C2791](compiler-error-c2791.md)|uso no válido de 'super': '*clase*' no tiene clases base|
|[Error del compilador C2792](compiler-error-c2792.md)|'super': esta palabra clave debe ir seguida por '::'|
|[Error del compilador C2793](compiler-error-c2793.md)|'*token*': siguiente token inesperado '::', identificador o la palabra clave 'operator' lo esperado|
|[Error del compilador C2794](compiler-error-c2794.md)|'*identificador*': no es un miembro de ninguna clase base directa o indirecta de '*clase*'|
|[Error del compilador C2795](compiler-error-c2795.md)|' super::*identificador*' no es una función miembro|
|Error del compilador C2796|'ref new' solo puede usarse para crear una instancia de un tipo WinRT|
|[Error del compilador C2797](compiler-error-c2797.md)|(Obsoleto) '*identificador*': no se implementa la inicialización de lista dentro de la lista de inicializadores de miembro o inicializador de miembro de datos no estáticos|
|[Error del compilador C2798](compiler-error-c2798.md)|' super::*identificador*' es ambiguo|
|Error del compilador C2799|'*identificador*': debe inicializarse un objeto de tipo de clase calificado constante sin un constructor predeterminado proporcionado por el usuario|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
