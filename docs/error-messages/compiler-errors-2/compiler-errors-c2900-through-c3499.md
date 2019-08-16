---
title: Errores del compilador de C2900 a C2999
ms.date: 04/21/2019
f1_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
helpviewer_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
ms.assetid: e3440738-e11b-4878-9ae3-6bc6c53ba461
ms.openlocfilehash: 5d443153582921775a72e5af647d65b102b80b0b
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857218"
---
# <a name="compiler-errors-c2900-through-c2999"></a>Errores del compilador de C2900 a C2999

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|Error del compilador de C2900|'*declarador*': las plantillas de función de miembro en clases de WinRT deben ser 'private', 'internal' o 'protected private'|
|Error del compilador C2901|'*identificador*': Una interfaz genérica o delegado no puede ser público|
|[Error del compilador C2902](compiler-error-c2902.md)|'*token*': inesperado token siguiente 'template/generic', se esperaba un identificador|
|[Error del compilador C2903](compiler-error-c2903.md)|'*identificador*': símbolo no es una plantilla de clase/generic ni una plantilla de función/generic|
|[Error del compilador C2904](compiler-error-c2904.md)|'*identificador*': nombre ya se usó para una plantilla en el ámbito actual|
|Error del compilador C2905|Obsoleto.|
|[Error del compilador C2906](compiler-error-c2906.md)|'*plantilla*': una especialización explícita requiere 'plantilla <>'|
|Error del compilador C2907|el argumento de registro '*número*' no especifica el número de registro válido|
|[Error del compilador C2908](compiler-error-c2908.md)|especialización explícita; '*plantilla*' ya se ha creado una instancia|
|[Error del compilador C2909](compiler-error-c2909.md)|'*identificador*': creación de instancias explícita de la plantilla de función requiere el tipo de valor devuelto|
|[Error del compilador C2910](compiler-error-c2910.md)|'*función*': no se puede especializar explícitamente|
|[Error del compilador C2911](compiler-error-c2911.md)|'*miembro*': no se puede declarar ni definir en el ámbito actual|
|[Error del compilador C2912](compiler-error-c2912.md)|especialización explícita '*declaración*' no es una especialización de una plantilla de función|
|[Error del compilador C2913](compiler-error-c2913.md)|especialización explícita; '*declaración*' no es una especialización de una plantilla de clase|
|[Error del compilador C2914](compiler-error-c2914.md)|'*identificador*': no se puede deducir el argumento de plantilla o genérico como argumento de función es ambigua|
|Error del compilador C2915|'*identificador*': '*tipo*' no se puede usar directamente en la superficie publicada de un tipo de WinRT. Use ' Platform:: Object ^' en su lugar para pasar este tipo|
|Error del compilador C2916|'*identificador*': [FlagsAttribute] (sólo) debe especificarse en una enumeración pública con 'unsigned int' tipo subyacente|
|[Error del compilador C2917](compiler-error-c2917.md)|'*identificador*': parámetro de plantilla no válido|
|[Error del compilador C2918](compiler-error-c2918.md)|'*identificador*': No se puede utilizar propiedades indizadas en la superficie publicada de un tipo WinRT|
|[Error del compilador C2919](compiler-error-c2919.md)|'*tipo*': No se puede usar operadores en la superficie publicada de un tipo WinRT|
|[Error del compilador C2920](compiler-error-c2920.md)|nueva definición: '*tipo*': clase de plantilla o genérico ya se ha declarado como*declaración*'|
|[Error del compilador C2921](compiler-error-c2921.md)|¡¡¡Redefinición: '*tipo*': clase de plantilla o genérico se está declarando de nuevo como*declaración*'|
|Error del compilador C2922|'*interfaz*': Una interfaz de WinRT no puede contener a miembros estáticos|
|[Error del compilador C2923](compiler-error-c2923.md)|'*tipo*': '*identificador*'no es un argumento de tipo template/generic válido para el parámetro'*parámetro*'|
|Error del compilador C2924|argumento de la rutina __declspec (interrupción) no está en R2|
|Error del compilador C2925|rutina __declspec (interrupción) no se puede utilizar punto flotante|
|Error del compilador C2926|'*identificador*': no se permite un inicializador de miembro predeterminado para un miembro de un struct anónimo dentro de una unión|
|[Error del compilador C2927](compiler-error-c2927.md)|'*identificador*': una plantilla de función debe llamarse con al menos un argumento|
|[Error del compilador C2928](compiler-error-c2928.md)|creación de instancias explícita; '*identificador*'no es una función o un miembro de datos estáticos de clase de plantilla'*clase*'|
|[Error del compilador C2929](compiler-error-c2929.md)|'*declarador*': creación de instancias explícita; explícitamente no se puede forzar y suprimir la creación de instancias de miembro de clase de plantilla|
|[Error del compilador C2930](compiler-error-c2930.md)|'*clase*':-id/genérico: Id. de plantilla se ha redefinido como un enumerador de ' enum *identificador*'|
|[Error del compilador C2931](compiler-error-c2931.md)|'*class1*':-id/genérico: Id. de plantilla se ha redefinido como una función miembro de '*class2*'|
|[Error del compilador C2932](compiler-error-c2932.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como un miembro de datos de '*identificador*'|
|[Error del compilador C2933](compiler-error-c2933.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como un miembro typedef de '*identificador*'|
|[Error del compilador C2934](compiler-error-c2934.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como anidada '*elemento*'de'*identificador*'|
|[Error del compilador C2935](compiler-error-c2935.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como función global|
|[Error del compilador C2936](compiler-error-c2936.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como una variable de datos global|
|[Error del compilador C2937](compiler-error-c2937.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como typedef global|
|Error del compilador C2938|'*identificador*': No se pudo especializar la plantilla de alias|
|[Error del compilador C2939](compiler-error-c2939.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como una variable de datos local|
|[Error del compilador C2940](compiler-error-c2940.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como typedef local|
|[Error del compilador C2941](compiler-error-c2941.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como una variable local '*elemento*'|
|[Error del compilador C2942](compiler-error-c2942.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como un argumento formal de una función|
|[Error del compilador C2943](compiler-error-c2943.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como un argumento de tipo de una plantilla|
|[Error del compilador C2944](compiler-error-c2944.md)|'*tipo*':-id/genérico: Id. de plantilla se ha redefinido como un argumento de valor de una plantilla|
|[Error del compilador C2945](compiler-error-c2945.md)|la creación de instancias explícita no hace referencia a una especialización de clase de plantilla|
|[Error del compilador C2946](compiler-error-c2946.md)|creación de instancias explícita; '*tipo*' no es una especialización de clase de plantilla|
|[Error del compilador C2947](compiler-error-c2947.md)|se esperaba ' >' para terminar los argumentos de plantilla, se encontró '*token*'|
|[Error del compilador C2948](compiler-error-c2948.md)|creación de instancias explícita; especificador de clase de almacenamiento '*especificador*' no permitido en la especialización|
|Error del compilador C2949|thread_local no se admite con /kernel|
|Error del compilador C2950|Obsoleto.|
|[Error del compilador C2951](compiler-error-c2951.md)|las declaraciones de plantilla o genérico solo se permiten en el espacio de nombres global, o ámbito de clase|
|[Error del compilador C2952](compiler-error-c2952.md)|'*declaración*': Falta lista de parámetros de plantilla o genérico de la declaración de plantilla o genérico|
|[Error del compilador C2953](compiler-error-c2953.md)|'*tipo*': ya se ha definido la plantilla de clase|
|Error del compilador C2954|argumento de palabra de instrucción fuera del intervalo|
|[Error del compilador C2955](compiler-error-c2955.md)|'*tipo*': uso de la clase de plantilla o genérico requiere la lista de argumentos de plantilla o genérico|
|Error del compilador C2956|desasignación con tamaño función 'operator delete (void *, size_t)' debe elegirse como función de desasignación de selección de ubicación.|
|[Error del compilador C2957](compiler-error-c2957.md)|'*token*': delimitador izquierdo no válido: se esperaba ' <'|
|[Error del compilador C2958](compiler-error-c2958.md)|la izquierda *delimitador* encontrado en '*archivo*(*line_number*)' no tiene correspondencia|
|[Error del compilador C2959](compiler-error-c2959.md)|una función o clase genérica no puede ser un miembro de una plantilla|
|Error del compilador C2960|Obsoleto.|
|Error del compilador C2961|'*función*': instancias explícitas incoherentes, una instancia explícita anterior no se especificó '*argumento*'|
|[Error del compilador C2962](compiler-error-c2962.md)|error de sintaxis: '*token*': se esperaba la definición de función miembro de clase de plantilla finalizase con '}'|
|Error del compilador C2963|Obsoleto.|
|Error del compilador C2964|Obsoleto.|
|Error del compilador C2965|__declspec (*especificador*) no se admite con /kernel|
|Error del compilador C2966|'*identificador1*': debe code_seg el mismo como su clase base*identificador2*'|
|Error del compilador C2967|'*identificador*': una función virtual de reemplazo debe tener el mismo __declspec(code_seg(...)) como una función virtual invalidada|
|Error del compilador C2968|'*identificador*': declaración de alias recursiva|
|[Error del compilador C2969](compiler-error-c2969.md)|error de sintaxis: '*token*': se esperaba la definición de función miembro finalizase con '}'|
|[Error del compilador C2970](compiler-error-c2970.md)|'*tipo*': parámetro de plantilla '*parámetro*': '*argumento*': no se puede usar una expresión que contenga objetos con vinculación interna como un argumento sin tipo|
|[Error del compilador C2971](compiler-error-c2971.md)|'*tipo*': parámetro de plantilla '*parámetro*': '*argumento*': no se puede usar una variable con una duración de almacenamiento no estática como un argumento sin tipo|
|Error del compilador C2972|'*tipo*': parámetro de plantilla '*parámetro*': el tipo del argumento de tipo no es válido|
|[Error del compilador C2973](compiler-error-c2973.md)|'*plantilla*': argumento de plantilla no válido '*número*'|
|[Error del compilador C2974](compiler-error-c2974.md)|'*tipo*': argumento de plantilla o genérico no válido para '*parámetro*', se esperaba un tipo|
|[Error del compilador C2975](compiler-error-c2975.md)|'*tipo*': argumento de plantilla no válido para '*parámetro*', se esperaba una expresión constante de tiempo de compilación|
|[Error del compilador C2976](compiler-error-c2976.md)|'*tipo*': demasiado pocos argumentos de plantilla o genérico|
|[Error del compilador C2977](compiler-error-c2977.md)|'*tipo*': hay demasiados argumentos de plantilla o genérico|
|[Error del compilador C2978](compiler-error-c2978.md)|error de sintaxis: se esperaba '*palabraclave1*'o'*palabraclave2*'; se encontró el tipo'*tipo*'; no son de tipo no se admiten parámetros en genéricos|
|[Error del compilador C2979](compiler-error-c2979.md)|no se admite especializaciones explícitas en genéricos|
|Error del compilador C2980|Control de excepciones de C++ no se admite con /kernel|
|Error del compilador C2981|la forma dinámica de '*palabra clave*' no se admite con /kernel|
|Error del compilador C2982|'*declaración*': distintos __declspec(code_seg(...)) usa: era '*identificador1*"ahora"*identificador2*'|
|Error del compilador C2983|'*declaración*': todas las declaraciones deben tener un __declspec(code_seg(...)) idénticos|
|Error del compilador C2984|Obsoleto.|
|Error del compilador C2985|'*argumento*': el argumento __declspec(code_seg(...)) debe ser una sección de texto|
|Error del compilador C2986|'*identificador*': solo puede aplicarse a una clase o una función __declspec(code_seg(...))|
|Error del compilador C2987|una declaración no puede tener tanto __declspec (code_seg ('*identificador*')) y __declspec (code_seg ('*valor*'))|
|[Error del compilador C2988](compiler-error-c2988.md)|declaración o definición de plantilla irreconocible|
|[Error del compilador C2989](compiler-error-c2989.md)|'*clase*': clase de plantilla o genérico ya se ha declarado como una plantilla que no son de clase/generic|
|[Error del compilador C2990](compiler-error-c2990.md)|'*clase*': ya se declaró una plantilla de clase/interfaz genérica que no son de clase de plantilla/generic|
|[Error del compilador C2991](compiler-error-c2991.md)|nueva definición del parámetro de plantilla o genérico '*parámetro*'|
|[Error del compilador C2992](compiler-error-c2992.md)|'*clase*': lista de parámetros de plantilla o genérico ausente o no válido|
|[Error del compilador C2993](compiler-error-c2993.md)|'*tipo*': tipo no válido para el parámetro de plantilla sin tipo '*identificador*'|
|[Error del compilador C2994](compiler-error-c2994.md)|clase sin nombre en la lista de parámetros de plantilla|
|[Error del compilador C2995](compiler-error-c2995.md)|'*declaración*': ya se ha definido la plantilla de función|
|[Error del compilador C2996](compiler-error-c2996.md)|'*función*': definición de plantilla de función recursiva|
|Error del compilador C2997|'*función*': no se puede deducir el límite de la matriz de un inicializador de miembro predeterminado|
|[Error del compilador C2998](compiler-error-c2998.md)|'*declarador*': no puede ser una definición de plantilla|
|Error del compilador C2999|ERROR DESCONOCIDO Elija el comando soporte técnico en el menú Ayuda de Visual C++, o abra el archivo de Ayuda de soporte técnico para obtener más información|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
