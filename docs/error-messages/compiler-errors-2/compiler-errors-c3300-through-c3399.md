---
title: Errores del compilador de C3300 a C3399
ms.date: 04/21/2019
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
ms.assetid: 190b7d29-ffe6-4261-921d-140da1935d00
ms.openlocfilehash: ca55e19534f722a7231a1d30c63e2dbb77d25ec7
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857733"
---
# <a name="compiler-errors-c3300-through-c3399"></a>Errores del compilador de C3300 a C3399

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|Error del compilador de C3300|'*símbolo*': formato incorrecto de IDL '*valor*'|
|Error del compilador C3301|'*coclase*': coclase no puede ser un '*símbolo*' interfaz|
|Error del compilador C3302|'*identificador*': identificador tiene más de *número* caracteres adicionales.|
|[Error del compilador C3303](compiler-error-c3303.md)|'*atributo*': atributo solo se puede usar en '*tipo*'|
|Error del compilador C3304|Obsoleto.|
|Error del compilador C3305|Obsoleto.|
|Error del compilador C3306|'*plantilla*': no se permite la plantilla de clase sin nombre/generic|
|Error del compilador C3307|'*módulo*': no se puede crear el módulo IDL|
|Error del compilador C3308|' *función*': no se admite la llamada a través de la clase importada directa|
|[Error del compilador C3309](compiler-error-c3309.md)|'*macro*/*palabra clave*': nombre del módulo no puede ser una macro ni una palabra clave|
|Error del compilador C3310|'*identificador*": conflicto de nombres de módulo|
|Error del compilador C3311|atributo de módulo se debe definir en el ámbito global|
|Error del compilador C3312|no invocable '*identificador*'función encuentra el tipo de'*tipo*'|
|Error del compilador C3313|'*identificador*': variable no puede tener el tipo '*tipo*'|
|Error del compilador C3314|'*símbolo*': no un tipo de módulo IDL admitido|
|Error del compilador C3315|' *función*': debe ser una función miembro|
|Error del compilador C3316|'*tipo*': una matriz de tamaño desconocido no se puede usar en basada en intervalo para la instrucción|
|Error del compilador C3317|'*identificador*': no se puede utilizar una función de sobrecarga como expresión de basada en intervalo para la instrucción|
|Error del compilador C3318|'*tipo*': una matriz no puede tener un tipo de elemento que contiene 'auto'|
|Error del compilador C3319|Obsoleto.|
|[Error del compilador C3320](compiler-error-c3320.md)|'*tipo*': tipo no puede tener el mismo nombre que la propiedad de módulo 'name'|
|Error del compilador C3321|una lista de inicializadores es inesperada en este contexto|
|[Error del compilador C3322](compiler-error-c3322.md)|'*propiedad*': no es una propiedad válida para el atributo '*atributo*'|
|Error del compilador C3323|'alignas' y '__declspec (Align)' no se permiten en declaraciones de función|
|Error del compilador C3324|'*propiedad*': propiedad aparece más de una vez en el atributo '*atributo*'|
|Error del compilador C3325|'*atributo*': el atributo tiene demasiados argumentos|
|Error del compilador C3326|'*valor*': no es un valor válido para la propiedad '*propiedad*'del atributo'*atributo*'|
|Error del compilador C3327|'*propiedad*': debe especificar el valor de propiedad del atributo '*atributo*'|
|Error del compilador C3328|'*atributo*': atributo no tiene argumentos suficientes|
|Error del compilador C3329|error de sintaxis: se esperaba '*token1*'not'*token2*'|
|Error del compilador C3330|' *función*': una función no puede devolver una matriz '*tipo*'|
|Error del compilador C3331|'*identificador*': solo se admiten atributos en los parámetros en coclases e interfaces COM|
|Error del compilador C3332|'*propiedad*': propiedad no es coherente, gramática '*propiedad*' es necesarios y tiene un valor predeterminado|
|[Error del compilador C3333](compiler-error-c3333.md)|'*biblioteca*': #import biblioteca de tipos dañada no se puede|
|[Error del compilador C3334](compiler-error-c3334.md)|una biblioteca de tipos dañada no se puede importar (#import)|
|Error del compilador C3335|'*identificador*': Puede haber como máximo una interfaz predeterminada para de una coclase*clase*'|
|Error del compilador C3336|Esta operación debe realizarse en el ámbito de clase|
|Error del compilador C3337|'*identificador*': defaultvtable debe ser un origen de eventos para de una coclase*clase*'|
|Error del compilador C3338|'*identificador*': Puede haber como máximo una interfaz predeterminada que es también un origen de eventos para de una coclase*clase*'|
|Error del compilador C3339|parámetro de plantilla requiere 'class' o 'typename' después de la lista de parámetros|
|[Error del compilador C3340](compiler-error-c3340.md)|'*identificador*': interfaz no puede ser 'restricted' y 'default' en la coclase*clase*'|
|Error del compilador C3341|'*interfaz*': una interfaz defaultvtable debe ser 'dual' o 'custom'|
|[Error del compilador C3342](compiler-error-c3342.md)|'*identificador*': atributo ambiguo|
|Error del compilador C3343|'*clase*::*nombre*': el identificador de atributo tiene demasiados caracteres|
|Error del compilador C3344|no se puede definir una especialización explícita ni una especialización parcial de '*símbolo*'|
|[Error del compilador C3345](compiler-error-c3345.md)|'*nombre*': identificador no válido para el nombre del módulo|
|Error del compilador C3346|declaración exportada en un ámbito que no sea espacio de nombres|
|[Error del compilador C3347](compiler-error-c3347.md)|'*argumento*': requiere el argumento no se especifica en el atributo *asttribute*|
|Error del compilador C3348|plantillas exportadas no forman parte de los estándares actuales de C++|
|Error del compilador C3349|'*clase*::*miembro*': atributo de multidifusión ya se ha implementado por el proveedor *proveedor*|
|[Error del compilador C3350](compiler-error-c3350.md)|' *función*': un constructor de delegado espera *número* argumento (s)|
|[Error del compilador C3351](compiler-error-c3351.md)|' *función*': si se pasa una instancia de objeto NULL a un constructor de delegado también se debe pasar la dirección de una función miembro estática|
|[Error del compilador C3352](compiler-error-c3352.md)|'*función*': la función especificada no coincide con el tipo delegado '*tipo*'|
|[Error del compilador C3353](compiler-error-c3353.md)|'*identificador*': un delegado solo puede crearse desde una función global o una función miembro de un tipo administrado o WinRT|
|[Error del compilador C3354](compiler-error-c3354.md)|'*identificador*': la función utilizada para crear un delegado no puede tener el tipo de valor devuelto '*tipo*'|
|Error del compilador C3355|'*clase*::*miembro*': atributo de multidifusión escucha al proveedor '*provider1*', pero es implementado por el proveedor '*McAfee2*'|
|[Error del compilador C3356](compiler-error-c3356.md)|'*identificador*': no se puede llamar a un atributo de multidifusión con un nombre completo|
|Error del compilador C3357|'*atributo*': atributo es ambiguo, debe utilizar un nombre completo|
|[Error del compilador C3358](compiler-error-c3358.md)|'*símbolo*': no se encontró el símbolo|
|Error del compilador C3359|'*especialización*': no se puede especializar la plantilla|
|[Error del compilador C3360](compiler-error-c3360.md)|'*cadena*': no se puede crear *nombre*|
|Error del compilador C3361|No hay ningún contexto en el que se va a *acción*|
|Error del compilador C3362|'*clase*::*miembro*': atributo de multidifusión no se ha implementado|
|[Error del compilador C3363](compiler-error-c3363.md)|'*identificador*': 'typeid' sólo puede aplicarse a un tipo|
|[Error del compilador C3364](compiler-error-c3364.md)|' *función*': argumento para constructor delegado no válido; debe ser un puntero a una función miembro de destino del delegado|
|[Error del compilador C3365](compiler-error-c3365.md)|operador '*operador*': diferencia de operandos de tipo '*tipo*'y'*tipo*'|
|[Error del compilador C3366](compiler-error-c3366.md)|'*miembro*': los miembros de datos estáticos de tipos administrados o WinRT deben definirse dentro de la definición de clase|
|[Error del compilador C3367](compiler-error-c3367.md)|' *función*': no se puede utilizar la función estática para crear un delegado sin enlazar|
|[Error del compilador C3368](compiler-error-c3368.md)|'*declarador*': convención de llamada no válida para IDL|
|[Error del compilador C3369](compiler-error-c3369.md)|'*módulo*': idl_module ya se definió|
|[Error del compilador C3370](compiler-error-c3370.md)|'*módulo*': idl_module aún no se ha definido|
|[Error del compilador C3371](compiler-error-c3371.md)|'idl_module': aquí solo se permite la propiedad 'name'|
|[Error del compilador C3372](compiler-error-c3372.md)|debe especificar al menos 1 interfaz para el atributo '*atributo*' en una coclase|
|[Error del compilador C3373](compiler-error-c3373.md)|atributo '*atributo*' no toma ningún argumento excepto en una coclase|
|[Error del compilador C3374](compiler-error-c3374.md)|no se puede adquirir la dirección de ' *función*' a menos que la creación de instancia de delegado|
|[Error del compilador C3375](compiler-error-c3375.md)|'*función*': función delegada ambigua|
|Error del compilador C3376|'*plantilla*': se permiten solo las plantillas de miembro de datos estáticos|
|Error del compilador C3377|no se permite 'decltype (Auto)' en una expresión new|
|Error del compilador C3378|una declaración se puede exportar sólo desde una unidad de la interfaz de módulo|
|[Error del compilador C3379](compiler-error-c3379.md)|'*clase*': una clase anidada no puede tener un especificador de acceso de ensamblado como parte de su declaración.|
|[Error del compilador C3380](compiler-error-c3380.md)|'*especificador*': especificador de acceso al ensamblado no válido se permite 'public' o 'private'|
|[Error del compilador C3381](compiler-error-c3381.md)|'*especificador*': los especificadores de acceso de ensamblado sólo están disponibles en el código compilado con la opción /clr|
|[Error del compilador C3382](compiler-error-c3382.md)|'sizeof' no se admite con /clr:safe|
|[Error del compilador C3383](compiler-error-c3383.md)|'operator new' no se admite con /clr:safe|
|[Error del compilador C3384](compiler-error-c3384.md)|'*tipo*': la restricción de valor y la restricción de referencia se excluyen mutuamente|
|[Error del compilador C3385](compiler-error-c3385.md)|' *función*': una función que tiene un atributo personalizado DllImport no puede devolver una instancia de una clase|
|[Error del compilador C3386](compiler-error-c3386.md)|'*tipo*': __declspec(dllexport)/__declspec(dllimport) no se puede aplicar a un tipo administrado o WinRT|
|[Error del compilador C3387](compiler-error-c3387.md)|'*miembro*': __declspec(dllexport)/__declspec(dllimport) no se puede aplicar a un miembro de un tipo administrado o WinRT|
|[Error del compilador C3388](compiler-error-c3388.md)|'*token*': no se permite como restricción, suponiendo que '*valor*' para continuar con el análisis|
|[Error del compilador C3389](compiler-error-c3389.md)|__declspec (*especificador*) no se puede usar con/CLR: pure o/CLR: safe|
|[Error del compilador C3390](compiler-error-c3390.md)|'*tipo*': argumento de tipo no válido para el parámetro genérico '*parámetro*'de genérico'*tipo_genérico*', debe ser un tipo de referencia|
|[Error del compilador C3391](compiler-error-c3391.md)|'*tipo*': argumento de tipo no válido para el parámetro genérico '*parámetro*'de genérico'*tipo_genérico*', debe ser un tipo de valor distinto de null|
|[Error del compilador C3392](compiler-error-c3392.md)|'*tipo*': argumento de tipo no válido para el parámetro genérico '*parámetro*'de genérico'*tipo_genérico*', debe tener un constructor público sin parámetros|
|[Error del compilador C3393](compiler-error-c3393.md)|error de sintaxis en la cláusula de restricción: '*identificador*' no es un tipo|
|[Error del compilador C3394](compiler-error-c3394.md)|error de sintaxis en la cláusula de restricción: se encontró '*símbolo*"se esperaba un tipo|
|[Error del compilador C3395](compiler-error-c3395.md)|' *función*': __declspec (dllexport) no se puede aplicar a una función con la convención de llamada __clrcall|
|[Error del compilador C3396](compiler-error-c3396.md)|'*clase*. *miembro*': atributo personalizado no se encuentra en '*espacio de nombres*'|
|[Error del compilador C3397](compiler-error-c3397.md)|No se permite la inicialización de agregado en argumentos predeterminados|
|[Error del compilador C3398](compiler-error-c3398.md)|'*operador*': no se puede convertir de '*tipo*'para'*tipo*'. La expresión de origen debe ser un símbolo de función|
|[Error del compilador C3399](compiler-error-c3399.md)|'*tipo*': no se puede proporcionar argumentos al crear una instancia de un parámetro genérico|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
