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
ms.openlocfilehash: f4aff80178033d34cf051a14d89736b2b8347dd0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446838"
---
# <a name="compiler-errors-c3400-through-c3499"></a>Errores del compilador de C3400 a C3499

En los artículos de esta sección de la documentación se explica un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Message|
|-----------|-------------|
|[Error del compilador C3400](compiler-error-c3400.md)|dependencia de restricción circular que implica '*constraint1*' y '*constraint2*'|
|Error del compilador C3401|'*Specifier*': especificador de acceso de ensamblado no válido; solo se permite ' Private ' en plantillas de clase|
|Error del compilador C3402|'*función*': no se puede resolver la sobrecarga excepto en el ámbito actual|
|Error del compilador C3403|no se puede usar thread_local con/CLR: Pure o/CLR: Safe|
|Error del compilador C3404|'*Construct*': error de sintaxis inesperado|
|Error del compilador C3405|'*función*': no se puede resolver la sobrecarga sin un descriptor completo|
|Error del compilador C3406|'*Keyword*': no se puede usar en un especificador de tipo elaborado|
|Error del compilador C3407|'*Type*' no se puede usar en este contexto|
|[Error del compilador C3408](compiler-error-c3408.md)|'*atributo*': no se permite el atributo en las definiciones de plantilla|
|[Error del compilador C3409](compiler-error-c3409.md)|no se permite un bloque de atributos vacío|
|Error del compilador C3410|'*Identifier*': el tipo de la creación de instancias explícita '*Type*' no coincide con el tipo de la plantilla de variable '*Type*'|
|Error del compilador C3411|'*Type*' no es válido como tamaño de una matriz, ya que no es un tipo entero|
|[Error del compilador C3412](compiler-error-c3412.md)|'*especialización*': no se puede especializar la plantilla en el ámbito actual|
|[Error del compilador C3413](compiler-error-c3413.md)|'*plantilla*': creación de instancias explícitas no válida|
|[Error del compilador C3414](compiler-error-c3414.md)|'*función*': no se puede definir la función miembro importada|
|[Error del compilador C3415](compiler-error-c3415.md)|se encontraron varias secciones '*section*' con atributos diferentes (' 0x*Value*')|
|Error del compilador ADVERTENCIA c3416|Obsoleto.|
|[Error del compilador C3417](compiler-error-c3417.md)|'*declarador*': los tipos de valor no pueden contener funciones miembro especiales definidas por el usuario|
|[Error del compilador C3418](compiler-error-c3418.md)|no se admite el especificador de acceso '*Specifier*'|
|Error del compilador C3419|Obsoleto.|
|[Error del compilador C3420](compiler-error-c3420.md)|'*función*': un finalizador no puede ser virtual|
|[Error del compilador C3421](compiler-error-c3421.md)|'*función*': no se puede llamar al finalizador para esta clase porque es inaccesible o no existe|
|Error del compilador C3422|'*declaration*': tipos no coincidentes '*Type*' y '*Type*'|
|Error del compilador C3423|Obsoleto.|
|Error del compilador C3424|'*Type*': no se permite una conversión de estilo de función a un tipo de matriz|
|Error del compilador C3425|no se puede iniciar un puntero a un objeto de tipo incompleto '*Type*'|
|Error del compilador C3426|no se puede producir un objeto de tipo incompleto '*Type*'|
|Error del compilador C3427|'*Context*': '*Keyword*' no se puede usar con layout_version (*número*)|
|Error del compilador C3428|'*Context*': '*Keyword*' solo se puede aplicar a definiciones o declaraciones de clase|
|Error del compilador C3429|'*Context*': '*Keyword*' no se puede aplicar a una Unión|
|Error del compilador C3430|una enumeración con ámbito debe tener un nombre|
|Error del compilador C3431|'*Identifier*': *Type1* no se puede volver a declarar como *tipo2*|
|Error del compilador C3432|'*Identifier*': una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente|
|Error del compilador C3433|'*Identifier*': todas las declaraciones de una enumeración deben tener el mismo tipo subyacente; era '*Type1*' ahora '*tipo2*'|
|Error del compilador C3434|'*Context*': el valor del enumerador '*Number*' no se puede representar como '*Type*'; el valor es '*Number*'|
|Error del compilador C3435|no se admite*el*juego de caracteres ' nombre '|
|Error del compilador C3436|#pragma setlocale no se admite cuando se ha especificado/Source-charset,/Execution-charset o/UTF-8|
|Error del compilador C3437|#pragma execution_character_set no se admite cuando se ha especificado/Source-charset,/Execution-charset o/UTF-8|
|Error del compilador C3438|'*Context*': '*Value*' no se puede aplicar a una clase administrada o WinRT|
|Error del compilador C3439|layout_version (*número*): número de versión no válido|
|Error del compilador C3440|'*declaration*': layout_version (*número*) incompatible con una declaración anterior|
|Error del compilador C3441|'*declaration*': '*Keyword*' no se puede aplicar después de haber definido la clase|
|Error del compilador C3442|Inicializando varios miembros de Union: '*member1*' y '*miembro2*'|
|Error del compilador C3443|El inicializador de miembro predeterminado para '*Class*' es recursivo|
|Error del compilador C3444|La clase de agregado vacía '*Class*' debe inicializarse con '{}'|
|[Error del compilador C3445](compiler-error-c3445.md)|la inicialización de lista de copia de '*tipo*' no puede usar un constructor explícito|
|[Error del compilador C3446](compiler-error-c3446.md)|'*Class*': no se permite un inicializador de miembro predeterminado para un miembro de una clase Value|
|Error del compilador C3447|Obsoleto.|
|Error del compilador C3448|Obsoleto.|
|Error del compilador C3449|Obsoleto.|
|[Error del compilador C3450](compiler-error-c3450.md)|'*Type*': no es un atributo; no se puede especificar [System:: AttributeUsageAttribute]/[Windows:: Foundation:: Metadata:: AttributeUsageAttribute]|
|[Error del compilador C3451](compiler-error-c3451.md)|'*Attribute*': no se puede aplicar un atributo no administrado a '*Type*'|
|[Error del compilador C3452](compiler-error-c3452.md)|miembro de lista de argumentos no constante|
|[Error del compilador C3453](compiler-error-c3453.md)|'*atributo*': atributo no aplicado porque el calificador '*Qualifier*' no coincidía|
|[Error del compilador C3454](compiler-error-c3454.md)|No se permite [attribute] en la declaración de clase|
|[Error del compilador C3455](compiler-error-c3455.md)|'*atributo*': ninguno de los constructores de atributo coincidía con los argumentos|
|[Error del compilador C3456](compiler-error-c3456.md)|[Source\_annotation_attribute] no se permite en la declaración de clase administrada o WinRT|
|[Error del compilador C3457](compiler-error-c3457.md)|'*atributo*': el atributo no admite argumentos sin nombre|
|[Error del compilador C3458](compiler-error-c3458.md)|' [*Attribute*] ': el atributo ' [*Attribute*] ' ya se especificó para '*Identifier*'|
|[Error del compilador C3459](compiler-error-c3459.md)|' [*Attribute*] ': el atributo solo se permite en el indizador de clase (propiedad indizada predeterminada)|
|[Error del compilador C3460](compiler-error-c3460.md)|'*Type*': solo se puede reenviar un tipo definido por el usuario|
|[Error del compilador C3461](compiler-error-c3461.md)|'*Type*': solo se puede reenviar un tipo administrado o WinRT|
|[Error del compilador C3462](compiler-error-c3462.md)|'*Type*': solo se puede reenviar un tipo importado|
|[Error del compilador C3463](compiler-error-c3463.md)|'*Type*': tipo no permitido en el atributo ' Implements '|
|[Error del compilador C3464](compiler-error-c3464.md)|'*Type*' no se puede reenviar un tipo anidado|
|[Error del compilador C3465](compiler-error-c3465.md)|para usar el tipo '*Type*' debe hacer referencia al ensamblado '*Assembly*'|
|[Error del compilador C3466](compiler-error-c3466.md)|'*Type*': no se puede reenviar una especialización de una clase genérica|
|[Error del compilador C3467](compiler-error-c3467.md)|'*Type*': este tipo ya se ha reenviado|
|[Error del compilador C3468](compiler-error-c3468.md)|'*Type*': solo se puede reenviar un tipo a un ensamblado: '*Identifier*' no es un ensamblado|
|[Error del compilador C3469](compiler-error-c3469.md)|'*Type*': no se puede reenviar una clase genérica|
|[Error del compilador C3470](compiler-error-c3470.md)|'*Class*': una clase no puede tener un indexador (propiedad indizada predeterminada) y un operador []|
|Error del compilador C3471|el nombre del nuevo *módulo (establecido* en la línea de comandos) entra en conflicto con *el* nombre anterior|
|Error del compilador C3472|el nuevo nombre del archivo de salida (establecido en la línea de comandos) entra en conflicto con *el nombre de* archivo anterior *nombreDeArchivo*|
|Error del compilador C3473|no se especificó ninguna ruta de la salida o nombre de módulo.|
|Error del compilador C3474|no se pudo abrir el archivo de salida '*nombreDeArchivo*'|
|Error del compilador C3475|error de sintaxis en el archivo de entrada '*nombreDeArchivo*'|
|Error del compilador C3476|no se pudo abrir el archivo '*nombreDeArchivo*' para la entrada|
|Error del compilador C3477|una expresión lambda no puede aparecer en un contexto no evaluado|
|Error del compilador C3478|'*Identifier*': la copia no puede capturar una matriz|
|Error del compilador C3479|No se admiten las anotaciones SAL en lambdas|
|[Error del compilador C3480](compiler-error-c3480.md)|'*variable*': una variable de captura lambda debe ser de un ámbito de función envolvente|
|[Error del compilador C3481](compiler-error-c3481.md)|'*Identifier*': no se encontró la variable de captura lambda|
|[Error del compilador C3482](compiler-error-c3482.md)|'this' solo se puede usar como captura lambda en una función miembro no estática|
|[Error del compilador C3483](compiler-error-c3483.md)|'*Identifier*' ya forma parte de la lista de capturas lambda|
|[Error del compilador error c3484](compiler-error-c3484.md)|error de sintaxis: se esperaba '-> ' antes del tipo de valor devuelto|
|[Error del compilador C3485](compiler-error-c3485.md)|una definición de lambda no puede tener ningún calificador cv|
|Error del compilador error c3486|Obsoleto.|
|[Error del compilador C3487](compiler-error-c3487.md)|'*Type*': todas las expresiones Return deben deducirse en el mismo tipo: antes era '*Type*'|
|[Error del compilador C3488](compiler-error-c3488.md)|' &*Identifier*' no se permite cuando el modo de captura predeterminado es por referencia|
|[Error del compilador C3489](compiler-error-c3489.md)|' &*Identifier*' es obligatorio cuando el modo de captura predeterminado es por copia|
|[Error del compilador C3490](compiler-error-c3490.md)|'*Identifier*' no se puede modificar porque se está accediendo a través de un objeto const|
|[Error del compilador error c3491](compiler-error-c3491.md)|'*Identifier*': una captura por copia no se puede modificar en una expresión lambda no mutable|
|[Error del compilador C3492](compiler-error-c3492.md)|'*Identifier*': no se puede capturar un miembro de una Unión anónima|
|[Error del compilador error c3493](compiler-error-c3493.md)|'*Identifier*' no se puede capturar de forma implícita porque no se ha especificado ningún modo de captura predeterminado|
|Error del compilador C3494|' this ' no se puede capturar explícitamente porque el modo de captura envolvente no lo permite|
|[Error del compilador C3495](compiler-error-c3495.md)|'*Identifier*': el identificador de la captura debe ser una variable con la duración de almacenamiento automática declarada en el ámbito de alcance de la expresión lambda|
|[Error del compilador C3496](compiler-error-c3496.md)|'this' siempre se captura por valor: se ha omitido '&'|
|Error del compilador C3497|no se puede construir una instancia de una expresión lambda|
|[Error del compilador C3498](compiler-error-c3498.md)|'*Identifier*': no se puede capturar una variable que tenga un tipo administrado o WinRT|
|[Error del compilador C3499](compiler-error-c3499.md)|una expresión lambda de la que se ha especificado que tiene un tipo de valor devuelto void no puede devolver un valor|

## <a name="see-also"></a>Consulte también

[Errores yC++ advertencias de las herramientas de compilación y del compilador de C/](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador C2000-C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
