---
title: Errores del compilador de C3400 a C3499
ms.date: 04/21/2019
f1_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3445
- C3446
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
helpviewer_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3445
- C3446
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
ms.assetid: a5651dfb-c402-4e01-b3ae-28f371e51d6a
ms.openlocfilehash: 587b28cedb0ab8b11c244be4278c7dc17d1f4247
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857378"
---
# <a name="compiler-errors-c3400-through-c3499"></a>Errores del compilador de C3400 a C3499

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C3400](compiler-error-c3400.md)|dependencia de restricción circular que implica '*constraint1*'y'*constraint2*'|
|Error del compilador C3401|'*especificador*': especificador de acceso de ensamblado no válido; solo 'private' se permite en las plantillas de clase|
|Error del compilador C3402|'*función*': no se puede resolver la sobrecarga, excepto en el ámbito actual|
|Error del compilador C3403|thread_local no se puede usar con/CLR: pure o/CLR: safe|
|Error del compilador C3404|'*construir*': error de sintaxis inesperado|
|Error del compilador C3405|'*función*': no se puede resolver la sobrecarga sin un descriptor completo|
|Error del compilador C3406|'*palabra clave*': no se puede usar en un especificador de tipo elaborado|
|Error del compilador C3407|'*tipo*' no se puede usar en este contexto|
|[Error del compilador C3408](compiler-error-c3408.md)|'*atributo*': atributo no se permite en las definiciones de plantilla|
|[Error del compilador C3409](compiler-error-c3409.md)|no se permite el bloque de atributos vacío|
|Error del compilador C3410|'*identificador*': el tipo de la creación de instancias explícita '*tipo*'no coincide con el tipo de la plantilla variable'*tipo*'|
|Error del compilador C3411|'*tipo*' no es válido como el tamaño de una matriz que no sea un tipo entero|
|[Error del compilador C3412](compiler-error-c3412.md)|'*especialización*': no se puede especializar la plantilla en el ámbito actual|
|[Error del compilador C3413](compiler-error-c3413.md)|'*plantilla*': creación de instancias explícita no válido|
|[Error del compilador C3414](compiler-error-c3414.md)|'*función*': no se puede definir la función miembro importada|
|[Error del compilador C3415](compiler-error-c3415.md)|varios '*sección*' secciones con atributos diferentes ('0 x*valor*')|
|Error del compilador C3416|Obsoleto.|
|[Error del compilador C3417](compiler-error-c3417.md)|'*declarador*': tipos de valor no pueden contener funciones miembro especiales definidas por el usuario|
|[Error del compilador C3418](compiler-error-c3418.md)|especificador de acceso '*especificador*' no se admite|
|Error del compilador C3419|Obsoleto.|
|[Error del compilador C3420](compiler-error-c3420.md)|'*función*': un finalizador no puede ser virtual|
|[Error del compilador C3421](compiler-error-c3421.md)|'*función*': no se puede llamar al finalizador para esta clase porque es inaccesible o no existe|
|Error del compilador C3422|'*declaración*': los tipos no coincidentes*tipo*'y'*tipo*'|
|Error del compilador C3423|Obsoleto.|
|Error del compilador C3424|'*tipo*': no se permite una conversión a un tipo de matriz de estilo de función|
|Error del compilador C3425|no se puede iniciar un puntero al objeto de tipo incompleto '*tipo*'|
|Error del compilador C3426|no se puede producir el objeto de tipo incompleto '*tipo*'|
|Error del compilador C3427|'*contexto*': '*palabra clave*' no se puede usar con layout_version (*número*)|
|Error del compilador C3428|'*contexto*': '*palabra clave*' solo se puede aplicar a definiciones o declaraciones de clase|
|Error del compilador C3429|'*contexto*': '*palabra clave*' no se puede aplicar a una unión|
|Error del compilador C3430|una enumeración con ámbito debe tener un nombre|
|Error del compilador C3431|'*identificador*': *type1* no se puede volver a declararse como *type2*|
|Error del compilador C3432|'*identificador*': una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente|
|Error del compilador C3433|'*identificador*': todas las declaraciones de enumeración debe tener el mismo tipo subyacente, era '*type1*"ahora"*type2*'|
|Error del compilador C3434|'*contexto*': valor de enumerador '*número*'no se puede representar como'*tipo*', valor es'*número*'|
|Error del compilador C3435|juego de caracteres '*nombre*' no se admite|
|Error del compilador C3436|#pragma setlocale no se admite cuando se ha especificado/Source-CharSet, / Execution-CharSet o/UTF-8|
|Error del compilador C3437|#pragma execution_character_set no se admite cuando se ha especificado/Source-CharSet, / Execution-CharSet o/UTF-8|
|Error del compilador C3438|'*contexto*': '*valor*' no se puede aplicar a una clase administrada o WinRT|
|Error del compilador C3439|layout_version(*number*): invalid version number|
|Error del compilador C3440|'*declaración*': layout_version (*número*) compatible con una declaración anterior|
|Error del compilador C3441|'*declaración*': '*palabra clave*' no se puede aplicar después de haber definido la clase|
|Error del compilador C3442|Inicializando varios miembros de unión: '*member1*'y'*member2*'|
|Error del compilador C3443|El inicializador de miembro predeterminado para '*clase*' es recursivo|
|Error del compilador C3444|Vacía la clase de agregado*clase*'debe inicializarse con'{}'|
|[Error del compilador C3445](compiler-error-c3445.md)|lista de inicialización de copia de '*tipo*' no se puede usar un constructor explícito|
|[Error del compilador C3446](compiler-error-c3446.md)|'*clase*': no se permite un inicializador de miembro predeterminado para un miembro de una clase value|
|Error del compilador C3447|Obsoleto.|
|Error del compilador C3448|Obsoleto.|
|Error del compilador C3449|Obsoleto.|
|[Error del compilador C3450](compiler-error-c3450.md)|'*tipo*': no es un atributo; no se puede especificar [System:: AttributeUsageAttribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute]|
|[Error del compilador C3451](compiler-error-c3451.md)|'*atributo*': no se puede aplicar el atributo no administrado a '*tipo*'|
|[Error del compilador C3452](compiler-error-c3452.md)|miembro de lista de argumentos no constante|
|[Error del compilador C3453](compiler-error-c3453.md)|'*atributo*': atributo no aplicado porque el calificador '*calificador*' no coincide con|
|[Error del compilador C3454](compiler-error-c3454.md)|No se permite [attribute] en la declaración de clase|
|[Error del compilador C3455](compiler-error-c3455.md)|'*atributo*': ninguno de los constructores de atributo coincidía con los argumentos|
|[Error del compilador C3456](compiler-error-c3456.md)|[origen\_annotation_attribute] no se permite en la declaración de clase administrada o WinRT|
|[Error del compilador C3457](compiler-error-c3457.md)|'*atributo*': atributo no admite argumentos sin nombre|
|[Error del compilador C3458](compiler-error-c3458.md)|' [*atributo*]': atributo ' [*atributo*]' ya especificada para '*identificador*'|
|[Error del compilador C3459](compiler-error-c3459.md)|' [*atributo*]': atributo solamente se permite en el indizador de clase (propiedad indizada predeterminada)|
|[Error del compilador C3460](compiler-error-c3460.md)|'*tipo*': se puede reenviar sólo un tipo definido por el usuario|
|[Error del compilador C3461](compiler-error-c3461.md)|'*tipo*': se puede reenviar un tipo administrado o WinRT|
|[Error del compilador C3462](compiler-error-c3462.md)|'*tipo*': se puede reenviar sólo un tipo importado|
|[Error del compilador C3463](compiler-error-c3463.md)|'*tipo*': tipo no permitido en el atributo 'implements'|
|[Error del compilador C3464](compiler-error-c3464.md)|'*tipo*' no se puede reenviar un tipo anidado|
|[Error del compilador C3465](compiler-error-c3465.md)|Para usar el tipo '*tipo*'debe hacer referencia al ensamblado'*ensamblado*'|
|[Error del compilador C3466](compiler-error-c3466.md)|'*tipo*': no se puede reenviar una especialización de una clase genérica|
|[Error del compilador C3467](compiler-error-c3467.md)|'*tipo*': este tipo ya se ha reenviado|
|[Error del compilador C3468](compiler-error-c3468.md)|'*tipo*': solamente puede reenviar un tipo a un ensamblado: '*identificador*' no es un ensamblado|
|[Error del compilador C3469](compiler-error-c3469.md)|'*tipo*': no se puede reenviar una clase genérica|
|[Error del compilador C3470](compiler-error-c3470.md)|'*clase*': una clase no puede tener un indizador (propiedad indizada predeterminada) y un operator]|
|Error del compilador C3471|nombre del nuevo módulo *nombre* (se configura en la línea de comandos) entra en conflicto con el nombre anterior *nombre*|
|Error del compilador C3472|nuevo nombre de archivo de salida *filename* (se configura en la línea de comandos) entra en conflicto con el nombre de archivo anterior *nombre de archivo*|
|Error del compilador C3473|salida pathname o módulo especificado ningún nombre.|
|Error del compilador C3474|no se pudo abrir el archivo de salida '*filename*'|
|Error del compilador C3475|error de sintaxis en el archivo de entrada '*filename*'|
|Error del compilador C3476|no se pudo abrir el archivo '*filename*' para la entrada|
|Error del compilador C3477|una expresión lambda no puede aparecer en un contexto no evaluado|
|Error del compilador C3478|'*identificador*': una matriz no se pueden capturar por copia|
|Error del compilador C3479|No se admiten anotaciones SAL en expresiones lambda|
|[Error del compilador C3480](compiler-error-c3480.md)|'*variable*': una variable de captura lambda debe ser un ámbito de inclusión (función)|
|[Error del compilador C3481](compiler-error-c3481.md)|'*identificador*': no se encontró la variable de captura de lambda|
|[Error del compilador C3482](compiler-error-c3482.md)|'this' solo se puede usar como captura lambda en una función miembro no estática|
|[Error del compilador C3483](compiler-error-c3483.md)|'*identificador*' ya forma parte de la lista de capturas lambda|
|[Error del compilador C3484](compiler-error-c3484.md)|error de sintaxis: se esperaba '->' antes del tipo de valor devuelto|
|[Error del compilador C3485](compiler-error-c3485.md)|una definición de lambda no puede tener ningún calificador cv|
|Error del compilador C3486|Obsoleto.|
|[Error del compilador C3487](compiler-error-c3487.md)|'*tipo*': todas devuelven expresiones deben deducirse como el mismo tipo: antes era '*tipo*'|
|[Error del compilador C3488](compiler-error-c3488.md)|' &*identificador*' no se permite cuando el modo de captura predeterminado es por referencia|
|[Error del compilador C3489](compiler-error-c3489.md)|' &*identificador*' es necesaria cuando el modo de captura predeterminado es por copia|
|[Error del compilador C3490](compiler-error-c3490.md)|'*identificador*' no se puede modificar porque se tiene acceso a través de un objeto const|
|[Error del compilador C3491](compiler-error-c3491.md)|'*identificador*': una copia captura no puede modificarse en una expresión lambda no mutable|
|[Error del compilador C3492](compiler-error-c3492.md)|'*identificador*': no se puede capturar un miembro de una unión anónima|
|[Error del compilador C3493](compiler-error-c3493.md)|'*identificador*' no se pueden capturar de forma implícita porque no se ha especificado ningún modo de captura predeterminado|
|Error del compilador C3494|'' no se puede capturar explícitamente porque no permite un modo de captura envolvente|
|[Error del compilador C3495](compiler-error-c3495.md)|'*identificador*': identificador de captura debe ser una variable con duración de almacenamiento automática declarada en el ámbito de alcance de la expresión lambda|
|[Error del compilador C3496](compiler-error-c3496.md)|'this' siempre se captura por valor: se ha omitido '&'|
|Error del compilador C3497|no se puede construir una instancia de una expresión lambda|
|[Error del compilador C3498](compiler-error-c3498.md)|'*identificador*': no se puede capturar una variable que tiene un tipo administrado o WinRT|
|[Error del compilador C3499](compiler-error-c3499.md)|una expresión lambda de la que se ha especificado que tiene un tipo de valor devuelto void no puede devolver un valor|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
