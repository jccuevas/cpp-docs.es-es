---
title: Compilador errores C3000 a C3099 | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
helpviewer_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
dev_langs:
- C++
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7565a2656bcb5c9ad10c83179b563423d42be7b5
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44319050"
---
# <a name="compiler-errors-c3000-through-c3099"></a>Compilador errores C3000 a C3099

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|C3000 de Error del compilador|Obsoleto.|
|[Error del compilador C3001](compiler-error-c3001.md)|'*mensaje*': se esperaba un nombre de la directiva de OpenMP|
|[Error del compilador C3002](compiler-error-c3002.md)|'*nombre1* *nombre2*': nombres de directiva de OpenMP múltiples|
|[Error del compilador C3003](compiler-error-c3003.md)|'*directiva*': nombre de la directiva de OpenMP no permitido después de las cláusulas de la directiva|
|[Error del compilador C3004](compiler-error-c3004.md)|'*cláusula*': cláusula no válida en OpenMP '*directiva*' directiva|
|[Error del compilador C3005](compiler-error-c3005.md)|'*mensaje*': símbolo (token) inesperado detectado en OpenMP '*directiva*' directiva|
|[Error del compilador C3006](compiler-error-c3006.md)|'*cláusula*': cláusula de OpenMP '*directiva*' falta un argumento esperado en la directiva|
|[Error del compilador C3007](compiler-error-c3007.md)|'*cláusula*': cláusula de OpenMP '*directiva*' directiva no toma un argumento|
|[Error del compilador C3008](compiler-error-c3008.md)|*argumento*': falta el argumento cierre ')' de OpenMP '*directiva*' directiva|
|[Error del compilador C3009](compiler-error-c3009.md)|'*etiqueta*': saltar dentro del bloque estructurado de OpenMP no permitido|
|[Error del compilador C3010](compiler-error-c3010.md)|'*etiqueta*': saltar fuera del bloque estructurado de OpenMP no permitido|
|[Error del compilador C3011](compiler-error-c3011.md)|no se permiten ensamblados alineados directamente dentro de una región paralela|
|[Error del compilador C3012](compiler-error-c3012.md)|'*función*': función intrínseca no permitida directamente dentro de una región paralela|
|[Error del compilador C3013](compiler-error-c3013.md)|'*cláusula*': cláusula solamente puede aparecer una vez en OpenMP '*directiva*' directiva|
|[Error del compilador C3014](compiler-error-c3014.md)|se esperaba un bucle for después de OpenMP '*directiva*' directiva|
|[Error del compilador C3015](compiler-error-c3015.md)|la forma de la inicialización de la instrucción 'for' de OpenMP no es adecuada|
|[Error del compilador C3016](compiler-error-c3016.md)|'*identificador*': variable de índice de la 'instrucción for' de OpenMP debe dispone de tipo entero con signo|
|[Error del compilador C3017](compiler-error-c3017.md)|la forma de la prueba de terminación de la instrucción 'for' de OpenMP no es adecuada|
|[Error del compilador C3018](compiler-error-c3018.md)|'*identificador*': OpenMP 'for' prueba o incremento debe usar la variable de índice '*variable*'|
|[Error del compilador C3019](compiler-error-c3019.md)|incremento de la 'instrucción for' de OpenMP tiene un formato incorrecto|
|[Error del compilador C3020](compiler-error-c3020.md)|'*variable*': variable de índice de 'bucle for' de OpenMP no puede modificarse en el cuerpo del bucle|
|[Error del compilador C3021](compiler-error-c3021.md)|'*argumento*': argumento está vacío en OpenMP '*directiva*' directiva|
|[Error del compilador C3022](compiler-error-c3022.md)|'*directiva*': tipo de programación no válida de '*directiva*'de OpenMP'*directiva*' directiva|
|[Error del compilador C3023](compiler-error-c3023.md)|'*argumento*': símbolo (token) inesperado en el argumento y OpenMP '*directiva*' cláusula|
|[Error del compilador C3024](compiler-error-c3024.md)|'Schedule (Runtime)': expresión chunk_size no permitida|
|[Error del compilador C3025](compiler-error-c3025.md)|'*cláusula*': se esperaba una expresión integral|
|[Error del compilador C3026](compiler-error-c3026.md)|'*cláusula*': expresión constante debe ser positiva|
|[Error del compilador C3027](compiler-error-c3027.md)|'*cláusula*': se esperaba una expresión aritmética o de puntero|
|[Error del compilador C3028](compiler-error-c3028.md)|'*miembro*': solo un miembro de datos estático o variable puede usarse en una cláusula de uso compartido de datos|
|[Error del compilador C3029](compiler-error-c3029.md)|'*símbolo*': solo puede aparecer una vez en el uso compartido de datos de las cláusulas de una directiva de OpenMP|
|[Error del compilador C3030](compiler-error-c3030.md)|'*identificador*': variable '*directiva*' cláusula o directiva no puede tener tipo de referencia|
|[Error del compilador C3031](compiler-error-c3031.md)|'*identificador*': la variable de la cláusula 'reduction' debe tener un tipo aritmético escalar|
|[Error del compilador C3032](compiler-error-c3032.md)|'*identificador*': variable '*cláusula*'cláusula no puede tener un tipo incompleto'*tipo*'|
|[Error del compilador C3033](compiler-error-c3033.md)|'*identificador*': variable '*cláusula*' cláusula no puede tener un tipo calificado constante|
|[Error del compilador C3034](compiler-error-c3034.md)|OpenMP '*directiva*'directiva no se puede anidar directamente dentro de'*directiva*' directiva|
|[Error del compilador C3035](compiler-error-c3035.md)|La directiva 'ordered' de OpenMP se debe enlazar directamente a una directiva 'for' o 'parallel for' con la cláusula 'ordered'|
|[Error del compilador C3036](compiler-error-c3036.md)|'*cláusula*': símbolo (token) de operador no válido en la cláusula 'Reduction' de OpenMP|
|[Error del compilador C3037](compiler-error-c3037.md)|'*identificador*': variable '*cláusula*' cláusula debe compartirse en el contexto envolvente|
|[Error del compilador C3038](compiler-error-c3038.md)|'*identificador*': la variable de la cláusula 'private' no puede ser una variable de reducción en el contexto envolvente|
|[Error del compilador C3039](compiler-error-c3039.md)|'*identificador*': variable de índice de la 'instrucción for' de OpenMP no puede ser una variable de reducción|
|[Error del compilador C3040](compiler-error-c3040.md)|'*identificador*': tipo de variable en la cláusula 'reduction' no es compatible con el operador de reducción '*operador*'|
|[Error del compilador C3041](compiler-error-c3041.md)|'*identificador*': la variable de la cláusula 'copyprivate' debe ser privada en el contexto envolvente|
|[Error del compilador C3042](compiler-error-c3042.md)|las cláusulas 'copyprivate' y 'nowait' no pueden aparecer juntas en OpenMP '*directiva*' directiva|
|[Error del compilador C3043](compiler-error-c3043.md)|la directiva 'critical' de OpenMP no se puede anidar en una directiva 'critical' con el mismo nombre|
|[Error del compilador C3044](compiler-error-c3044.md)|'section': solo permite anida directamente bajo una directiva 'sections' de OpenMP|
|[Error del compilador C3045](compiler-error-c3045.md)|Se esperaba una instrucción compuesta después de la directiva 'sections' de OpenMP. Falta '{'|
|[Error del compilador C3046](compiler-error-c3046.md)|Falta el bloque estructurado en la región '#pragma omp sections' de OpenMP|
|[Error del compilador C3047](compiler-error-c3047.md)|El bloque estructurado en la región 'sections' de OpenMP debe ir precedido de '#pragma omp section'|
|[Error del compilador C3048](compiler-error-c3048.md)|la forma de la expresión que va después de '#pragma omp atomic' no es adecuada|
|[Error del compilador C3049](compiler-error-c3049.md)|'*argumento*': argumento no válido en la cláusula 'default' de OpenMP|
|[Error del compilador C3050](compiler-error-c3050.md)|'*clase*': una clase ref no puede heredar de '*identificador*'|
|C3051 de Error del compilador|Obsoleto.|
|[Error del compilador C3052](compiler-error-c3052.md)|'*identificador*': variable no aparece en una cláusula de uso compartido de datos bajo una cláusula default (None)|
|[Error del compilador C3053](compiler-error-c3053.md)|'*identificador*': 'threadprivate' solo es válido para elementos de datos globales o estáticos|
|[Error del compilador C3054](compiler-error-c3054.md)|'#pragma omp parallel' actualmente es incompatible en una función o clase genérica|
|[Error del compilador C3055](compiler-error-c3055.md)|'*identificador*': no se hace referencia al símbolo antes de utilizarse en la directiva 'threadprivate'|
|[Error del compilador C3056](compiler-error-c3056.md)|'*identificador*': símbolo no está en el mismo ámbito con la directiva 'threadprivate'|
|[Error del compilador C3057](compiler-error-c3057.md)|'*identificador*': inicialización dinámica de los símbolos 'threadprivate' no se admite actualmente|
|[Error del compilador C3058](compiler-error-c3058.md)|'*identificador*': símbolo no declarado como 'threadprivate' antes de utilizarse en la cláusula 'copyin'|
|[Error del compilador C3059](compiler-error-c3059.md)|'*identificador*': símbolo 'threadprivate' no se puede usar en el '*cláusula*' cláusula|
|[Error del compilador C3060](compiler-error-c3060.md)|'*identificador*': no se puede definir una función friend dentro de una clase mediante un nombre completo (solamente se puede declarar)|
|C3061 de Error del compilador|operador '*operador*': no se permite en la enumeración '*tipo*'con el tipo subyacente'*tipo*'|
|[Error del compilador C3062](compiler-error-c3062.md)|'*identificador*': enumerador requiere un valor porque el tipo subyacente es '*tipo*'|
|[Error del compilador C3063](compiler-error-c3063.md)|operador '*operador*': todos los operandos deben tener el mismo tipo de enumeración|
|C3064 de Error del compilador|'*identificador*': debe ser un tipo simple o resolverse en uno|
|[Error del compilador C3065](compiler-error-c3065.md)|no se permite la declaración de propiedad en un ámbito que no es de clase|
|[Error del compilador C3066](compiler-error-c3066.md)|Hay varias maneras de que un objeto de este tipo se puede llamar con estos argumentos|
|C3067 de Error del compilador|no se puede usar una lista de inicializadores con el operador integrado]|
|[Error del compilador C3068](compiler-error-c3068.md)|'*identificador*': una función 'naked' no puede contener objetos que requerirían desenredo si se ha producido una excepción de C++|
|[Error del compilador C3069](compiler-error-c3069.md)|operador '*operador*': no se permite para el tipo de enumeración|
|[Error del compilador C3070](compiler-error-c3070.md)|'*identificador*': propiedad no tiene un método 'set'|
|[Error del compilador C3071](compiler-error-c3071.md)|operador '*operador*' solo puede aplicarse a una instancia de una clase ref o un tipo de valor|
|[Error del compilador C3072](compiler-error-c3072.md)|operador '*operador*' no se puede aplicar a una instancia de un uso de clase ref, el operador unario '%' para convertir una instancia de una referencia a un tipo de identificador de clase|
|[Error del compilador C3073](compiler-error-c3073.md)|'*identificador*': clase ref no tiene un constructor de copias definido por el usuario|
|C3074 de Error del compilador|no se puede inicializar una matriz con un inicializador entre paréntesis|
|[Error del compilador C3075](compiler-error-c3075.md)|'*identificador*': no se puede incrustar una instancia de un tipo de referencia, '*tipo*', en un tipo de valor|
|[Error del compilador C3076](compiler-error-c3076.md)|'*identificador*': no se puede incrustar una instancia de un tipo de referencia, '*tipo*', en un tipo nativo|
|[Error del compilador C3077](compiler-error-c3077.md)|'*identificador*': un finalizador solamente puede ser un miembro de un tipo de referencia|
|C3078 de Error del compilador|se debe especificar el tamaño de la matriz en nuevas expresiones|
|C3079 de Error del compilador|no se puede usar una lista de inicializadores como operando derecho de este operador de asignación|
|[Error del compilador C3080](compiler-error-c3080.md)|'*finalizador*': un finalizador no puede tener un especificador de clase de almacenamiento|
|C3081 de Error del compilador|Obsoleto.|
|Error del compilador C3082|Obsoleto.|
|[Error del compilador C3083](compiler-error-c3083.md)|'*identificador*': el símbolo a la izquierda de un '::' debe ser un tipo|
|[Error del compilador C3084](compiler-error-c3084.md)|'*identificador*': un destructor/finalizador no puede ser '*palabra clave*'|
|[Error del compilador C3085](compiler-error-c3085.md)|'*identificador*': un constructor no puede ser '*palabra clave*'|
|C3086 de Error del compilador|no se encuentra 'std:: initializer_list': debe #include \<initializer_list >|
|[Error del compilador C3087](compiler-error-c3087.md)|'*identificador*': llamada de '*declaración*' ya inicializa este miembro|
|C3088 de Error del compilador|'*clase*': constructor de atributo debe tener argumentos formales con nombre|
|C3089 de Error del compilador|'*identificador*': nombre de parámetro no coincide con el nombre de cualquier miembro de datos|
|C3090 de Error del compilador|'*clase*': clase de atributo no puede ser una plantilla|
|C3091 de Error del compilador|'*clase*': clase de atributo no puede tener clases base|
|C3092 de Error del compilador|'*clase*': miembro de clase de atributo no puede ser un poco campo, 'static' o 'const'|
|C3093 de Error del compilador|'*tipo*': tipo no permitido para el miembro de clase de atributo '*miembro*'|
|[Error del compilador C3094](compiler-error-c3094.md)|'*atributo*': uso anónimo no permitido|
|[Error del compilador C3095](compiler-error-c3095.md)|'*atributo*': no se puede repetir el atributo|
|[Error del compilador C3096](compiler-error-c3096.md)|'*atributo*': atributo se permite en miembros de datos de las clases de atributos|
|[Error del compilador C3097](compiler-error-c3097.md)|'*atributo*': ámbito del atributo debe ser ' ensamblado:' o ' module:'|
|C3098 de Error del compilador|'*identificador*': atributo no tiene ningún constructor definido por el usuario|
|[Error del compilador C3099](compiler-error-c3099.md)|'*palabra clave*': use [System:: AttributeUsageAttribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute] para atributos administrados o WinRT|
