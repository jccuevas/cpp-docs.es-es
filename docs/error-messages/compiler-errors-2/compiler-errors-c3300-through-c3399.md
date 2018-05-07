---
title: C3300 de errores del compilador a través de la advertencia C3399 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3300
- C3301
- C3302
- C3304
- C3305
- C3306
- C3307
- C3308
- C3310
- C3311
- C3312
- C3313
- C3314
- C3315
- C3316
- C3317
- C3318
- C3319
- C3321
- C3323
- C3324
- C3325
- C3326
- C3327
- C3328
- C3329
- C3330
- C3331
- C3332
- C3335
- C3336
- C3337
- C3338
- C3339
- C3341
- C3343
- C3344
- C3346
- C3348
- C3349
- C3355
- C3357
- C3359
- C3361
- C3362
- C3376
- C3377
- C3378
helpviewer_keywords:
- C3300
- C3301
- C3302
- C3304
- C3305
- C3306
- C3307
- C3308
- C3310
- C3311
- C3312
- C3313
- C3314
- C3315
- C3316
- C3317
- C3318
- C3319
- C3321
- C3323
- C3324
- C3325
- C3326
- C3327
- C3328
- C3329
- C3330
- C3331
- C3332
- C3335
- C3336
- C3337
- C3338
- C3339
- C3341
- C3343
- C3344
- C3346
- C3348
- C3349
- C3355
- C3357
- C3359
- C3361
- C3362
- C3376
- C3377
- C3378
dev_langs:
- C++
ms.assetid: 190b7d29-ffe6-4261-921d-140da1935d00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c5976e57e0a3b7f51c9df3fbdf3ebebb08dd1b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-errors-c3300-through-c3399"></a>C3300 de errores del compilador a través de la advertencia C3399

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|C3300 de Error del compilador|'*símbolo*': formato incorrecto de IDL '*valor*'|
|C3301 de Error del compilador|'*coclase*': coclase no puede ser un '*símbolo*' interfaz|
|C3302 de Error del compilador|'*identificador*': identificador tiene más de *número* caracteres|
|[Error del compilador C3303](compiler-error-c3303.md)|'*atributo*': atributo solo se puede usar en '*tipo*'|
|Error del compilador C3304|Obsoleto.|
|Error del compilador C3305|Obsoleto.|
|C3306 de Error del compilador|'*plantilla*': no se permite la plantilla de clase sin nombre/generic|
|C3307 de Error del compilador|'*módulo*': no se puede crear el módulo IDL|
|C3308 de Error del compilador|' *función*': directa no se admite la llamada a través de la clase importada|
|[Error del compilador C3309](compiler-error-c3309.md)|'*macro*/*palabra clave*': nombre de módulo no puede ser una macro ni una palabra clave|
|C3310 de Error del compilador|'*identificador*': conflicto de nombres de módulo|
|C3311 de Error del compilador|atributo de módulo debe definirse en el ámbito global|
|C3312 de Error del compilador|no se puede llamar '*identificador*'función encuentra para el tipo'*tipo*'|
|C3313 de Error del compilador|'*identificador*': variable no puede tener el tipo '*tipo*'|
|C3314 de Error del compilador|'*símbolo*': no un tipo de módulo IDL admitido|
|C3315 de Error del compilador|' *función*': debe ser una función miembro|
|C3316 de Error del compilador|'*tipo*': no se puede usar una matriz de tamaño desconocido en basado en un intervalo de instrucción|
|C3317 de Error del compilador|'*identificador*': no se puede usar una función de sobrecarga que la expresión de basado en un intervalo de instrucción|
|C3318 de Error del compilador|'*tipo*': una matriz no puede tener un tipo de elemento que contiene 'auto'|
|C3319 de Error del compilador|Obsoleto.|
|[Error del compilador C3320](compiler-error-c3320.md)|'*tipo*': tipo no puede tener el mismo nombre que la propiedad de módulo 'name'|
|C3321 de Error del compilador|una lista de inicializadores es inesperada en este contexto|
|[Error del compilador C3322](compiler-error-c3322.md)|'*propiedad*': no es una propiedad válida para el atributo '*atributo*'|
|C3323 de Error del compilador|'alignas' y '__declspec (Align)' no se permiten en las declaraciones de función|
|C3324 de Error del compilador|'*propiedad*': propiedad aparece más de una vez en el atributo '*atributo*'|
|C3325 de Error del compilador|'*atributo*': el atributo tiene demasiados argumentos|
|C3326 de Error del compilador|'*valor*': no es un valor válido para la propiedad '*propiedad*'del atributo'*atributo*'|
|C3327 de Error del compilador|'*propiedad*': debe especificar el valor de propiedad de atributo '*atributo*'|
|C3328 de Error del compilador|'*atributo*': atributo no tiene suficientes argumentos|
|C3329 de Error del compilador|error de sintaxis: se esperaba '*símbolo1*'not'*token2*'|
|C3330 de Error del compilador|' *función*': una función no puede devolver una matriz '*tipo*'|
|C3331 de Error del compilador|'*identificador*': atributos en parámetros sólo se permiten en coclases e interfaces COM|
|C3332 de Error del compilador|'*propiedad*': no es coherente, propiedad de gramática '*propiedad*' es necesarios y tiene una restricción default|
|[Error del compilador C3333](compiler-error-c3333.md)|'*biblioteca*': #import biblioteca de tipos dañada no se puede|
|[Error del compilador C3334](compiler-error-c3334.md)|una biblioteca de tipos dañada no se puede importar (#import)|
|C3335 de Error del compilador|'*identificador*': puede haber a lo sumo una interfaz predeterminada para una coclase*clase*'|
|C3336 de Error del compilador|Esta operación debe realizarse en el ámbito de clase|
|C3337 de Error del compilador|'*identificador*': defaultvtable debe ser un origen de eventos para una coclase*clase*'|
|C3338 de Error del compilador|'*identificador*': puede haber a lo sumo una interfaz predeterminada que sea también un origen de eventos para una coclase*clase*'|
|C3339 de Error del compilador|parámetro de plantilla requiere 'class' o 'typename' después de la lista de parámetros|
|[Error del compilador C3340](compiler-error-c3340.md)|'*identificador*': interfaz no puede ser 'restricted' y 'default' en la coclase*clase*'|
|C3341 de Error del compilador|'*interfaz*': una interfaz defaultvtable debe ser 'dual' o 'custom'|
|[Error del compilador C3342](compiler-error-c3342.md)|'*identificador*': atributo ambiguo|
|C3343 de Error del compilador|'*clase*::*nombre*': el identificador de atributo tiene demasiados caracteres|
|C3344 de Error del compilador|no se puede definir una especialización explícita ni una especialización parcial de '*símbolo*'|
|[Error del compilador C3345](compiler-error-c3345.md)|'*nombre*': identificador no válido para el nombre del módulo|
|C3346 de Error del compilador|declaración exportado en el ámbito de espacio de nombres no|
|[Error del compilador C3347](compiler-error-c3347.md)|'*argumento*': requiere el argumento no se especifica en el atributo *asttribute*|
|C3348 de Error del compilador|plantillas exportadas no forman parte de los estándares actuales de C++|
|C3349 de Error del compilador|'*clase*::*miembro*': ya se ha implementado el atributo de multidifusión por proveedor *proveedor*|
|[Error del compilador C3350](compiler-error-c3350.md)|' *función*': un constructor de delegado espera *número* argumentos|
|[Error del compilador C3351](compiler-error-c3351.md)|' *función*': si se pasa una instancia de objeto NULL a un constructor de delegado también se debe pasar la dirección de una función miembro estática|
|[Error del compilador C3352](compiler-error-c3352.md)|'*función*': la función especificada no coincide con el tipo de delegado '*tipo*'|
|[Error del compilador C3353](compiler-error-c3353.md)|'*identificador*': un delegado solo puede crearse desde una función global o una función miembro de un tipo administrado o WinRT|
|[Error del compilador C3354](compiler-error-c3354.md)|'*identificador*': la función que se usa para crear un delegado no puede tener el tipo de valor devuelto '*tipo*'|
|C3355 de Error del compilador|'*clase*::*miembro*': atributo de multidifusión escucha al proveedor '*Proveedor1*', pero se implementa mediante el proveedor '*PROVEEDOR2*'|
|[Error del compilador C3356](compiler-error-c3356.md)|'*identificador*': no se puede llamar a un atributo de multidifusión con un nombre completo|
|C3357 de Error del compilador|'*atributo*': atributo es ambiguo, debe utilizar el nombre completo|
|[Error del compilador C3358](compiler-error-c3358.md)|'*símbolo*': no se encontró el símbolo|
|C3359 de Error del compilador|'*especialización*': no se puede especializar la plantilla|
|[Error del compilador C3360](compiler-error-c3360.md)|'*cadena*': no se puede crear *nombre*|
|C3361 de Error del compilador|No hay ningún contexto en el que se va a *acción*|
|C3362 de Error del compilador|'*clase*::*miembro*': no se implementó el atributo de multidifusión|
|[Error del compilador C3363](compiler-error-c3363.md)|'*identificador*': 'typeid' solo puede aplicarse a un tipo|
|[Error del compilador C3364](compiler-error-c3364.md)|' *función*': argumento no válido para el constructor de delegado; delegado debe ser un puntero a una función miembro de destino|
|[Error del compilador C3365](compiler-error-c3365.md)|operador '*operador*': diferencia de operandos de tipo '*tipo*'y'*tipo*'|
|[Error del compilador C3366](compiler-error-c3366.md)|'*miembro*': los miembros de datos estáticos de tipos administrados o WinRT se deben definir dentro de la definición de clase|
|[Error del compilador C3367](compiler-error-c3367.md)|' *función*': no se puede usar la función estática para crear un delegado sin enlazar|
|[Error del compilador C3368](compiler-error-c3368.md)|'*declarador*': convención llamada no válida para IDL|
|[Error del compilador C3369](compiler-error-c3369.md)|'*módulo*': idl_module ya se definió|
|[Error del compilador C3370](compiler-error-c3370.md)|'*módulo*': idl_module aún no se ha definido|
|[Error del compilador C3371](compiler-error-c3371.md)|'idl_module': aquí solo se permite la propiedad 'name'|
|[Error del compilador C3372](compiler-error-c3372.md)|debe especificar al menos 1 interfaz para el atributo '*atributo*' en una coclase|
|[Error del compilador C3373](compiler-error-c3373.md)|atributo '*atributo*' no toma ningún argumento excepto en una coclase|
|[Error del compilador C3374](compiler-error-c3374.md)|no se puede adquirir la dirección de ' *función*' a menos que la creación de instancia del delegado|
|[Error del compilador C3375](compiler-error-c3375.md)|'*función*': función delegada ambigua|
|C3376 de Error del compilador|'*plantilla*': se permiten solo plantillas de miembro de datos estáticos|
|C3377 de Error del compilador|no se permite 'decltype (Auto)' en una expresión new|
|C3378 de Error del compilador|una declaración se pueden exportar sólo desde una unidad de interfaz de módulo|
|[Error del compilador C3379](compiler-error-c3379.md)|'*clase*': una clase anidada no puede tener un especificador de acceso de ensamblado como parte de su declaración|
|[Error del compilador C3380](compiler-error-c3380.md)|'*especificador*': especificador de acceso al ensamblado no válido se permite 'public' o 'private'|
|[Error del compilador C3381](compiler-error-c3381.md)|'*especificador*': los especificadores de acceso al ensamblado sólo están disponibles en el código compilado con la opción /clr|
|[Error del compilador C3382](compiler-error-c3382.md)|'sizeof' no se admite con /clr:safe|
|[Error del compilador C3383](compiler-error-c3383.md)|'operator new' no se admite con /clr:safe|
|[Error del compilador C3384](compiler-error-c3384.md)|'*tipo*': la restricción de valor y de referencia son mutuamente excluyentes|
|[Error del compilador C3385](compiler-error-c3385.md)|' *función*': una función que tiene un atributo personalizado DllImport no puede devolver una instancia de una clase|
|[Error del compilador C3386](compiler-error-c3386.md)|'*tipo*': __declspec(dllexport)/__declspec(dllimport) no se puede aplicar a un tipo administrado o WinRT|
|[Error del compilador C3387](compiler-error-c3387.md)|'*miembro*': __declspec(dllexport)/__declspec(dllimport) no se puede aplicar a un miembro de un tipo administrado o WinRT|
|[Error del compilador C3388](compiler-error-c3388.md)|'*token*': no se permite como restricción, suponiendo que '*valor*' para continuar con el análisis|
|[Error del compilador C3389](compiler-error-c3389.md)|__declspec (*especificador*) no se puede usar con/CLR: pure o/CLR: safe|
|[Error del compilador C3390](compiler-error-c3390.md)|'*tipo*': argumento de tipo no válido para el parámetro genérico '*parámetro*'de genérico'*tipo_genérico*', debe ser un tipo de referencia|
|[Error del compilador C3391](compiler-error-c3391.md)|'*tipo*': argumento de tipo no válido para el parámetro genérico '*parámetro*'de genérico'*tipo_genérico*', debe ser un tipo de valor no acepta valores null|
|[Error del compilador C3392](compiler-error-c3392.md)|'*tipo*': argumento de tipo no válido para el parámetro genérico '*parámetro*'de genérico'*tipo_genérico*', debe tener un constructor sin parámetros público.|
|[Error del compilador C3393](compiler-error-c3393.md)|error de sintaxis en la cláusula de restricción: '*identificador*' no es un tipo|
|[Error del compilador C3394](compiler-error-c3394.md)|error de sintaxis en la cláusula de restricción: se encontró '*símbolo*' se esperaba un tipo.|
|[Error del compilador C3395](compiler-error-c3395.md)|' *función*': __declspec (dllexport) no se puede aplicar a una función con la convención de llamada __clrcall|
|[Error del compilador C3396](compiler-error-c3396.md)|'*clase*. *miembro*': atributo personalizado no se encuentra en '*espacio de nombres*'|
|[Error del compilador C3397](compiler-error-c3397.md)|No se permite la inicialización de agregado en argumentos predeterminados|
|[Error del compilador C3398](compiler-error-c3398.md)|'*operador*': no se puede convertir de '*tipo*'to'*tipo*'. La expresión de origen debe ser un símbolo de función|
|[Error del compilador C3399](compiler-error-c3399.md)|'*tipo*': no se puede proporcionar argumentos cuando se crea una instancia de un parámetro genérico|
