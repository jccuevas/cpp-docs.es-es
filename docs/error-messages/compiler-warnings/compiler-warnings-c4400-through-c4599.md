---
title: Advertencias del compilador de C4400 a C4599
ms.date: 04/21/2019
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4452
- C4453
- C4454
- C4455
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
helpviewer_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
ms.openlocfilehash: 9f7886a88ebd98d5d7ab1848ea7a788967362ad7
ms.sourcegitcommit: d3829ae0c3db909f96057755a80665f5ea4896ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550447"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>Advertencias del compilador de C4400 a C4599

En los artículos de esta sección de la documentación se explica un subconjunto de los mensajes de advertencia generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Mensajes de advertencia

|Advertencia|Message|
|-------------|-------------|
|[ADVERTENCIA del compilador (nivel 1) C4600](compiler-warning-level-1-c4600.md)|#pragma '*macro Name*': se esperaba una cadena no vacía válida|
|[ADVERTENCIA del compilador (nivel 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'*Type*': no se admiten calificadores const/volatile en este tipo|
|[ADVERTENCIA del compilador (nivel 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'bits ': el miembro es un campo de bits|
|[ADVERTENCIA del compilador (nivel 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|debe usar el Operador PTR|
|[ADVERTENCIA del compilador (nivel 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|Operador PTR no válido|
|[ADVERTENCIA del compilador (nivel 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|se omitió el período de la Directiva|
|[ADVERTENCIA del compilador (nivel 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*Identifier*': el identificador es una palabra reservada|
|[ADVERTENCIA del compilador (nivel 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|operando de la Directiva omitido|
|[ADVERTENCIA del compilador (nivel 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|conversión entre diferentes representaciones de puntero a miembro, el compilador puede generar código incorrecto|
|[ADVERTENCIA del compilador (nivel 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|' struct&#124;Union ' anónimo no ha declarado ningún miembro de datos|
|[ADVERTENCIA del compilador (nivel 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|tamaño de instrucción no válido|
|[ADVERTENCIA del compilador (nivel 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|tamaño no válido para el operando|
|[ADVERTENCIA del compilador (nivel 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*Identifier*': el símbolo se resuelve como un registro de desplazamiento|
|[ADVERTENCIA del compilador (nivel 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*función*': la firma de la función contiene el tipo '*tipo*'; C++ los objetos no son seguros para pasar entre código puro y mixto o nativo.|
|ADVERTENCIA del compilador C4413|' className:: Member ': el miembro de referencia se inicializa en un temporal que no se conserva después de que se cierre el constructor|
|[ADVERTENCIA del compilador (nivel 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*función*': salto corto a función convertida en near|
|ADVERTENCIA del compilador (nivel 1) C4415|duplicado _ _ declspec (code_seg ('*Name*'))|
|ADVERTENCIA del compilador (nivel 1) C4416|_ _ declspec (code_seg (...)) contiene una cadena vacía: omitida|
|ADVERTENCIA del compilador (nivel 1) C4417|una creación de instancias de plantilla explícita no puede tener _ _ declspec (code_seg (...)): omitido|
|ADVERTENCIA del compilador (nivel 1) C4418|_ _ declspec (code_seg (...)) omitido en una enumeración|
|ADVERTENCIA del compilador (nivel 3) C4419|'*Symbol*' no tiene ningún efecto cuando se aplica a la clase Ref privada '*clase*'.|
|[ADVERTENCIA del compilador (nivel 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*': operador no disponible; se usará '*Operator*' en su lugar; la comprobación en tiempo de ejecución puede verse comprometida|
|ADVERTENCIA del compilador (nivel 3) C4421|'*parámetro*': un parámetro de referencia en una función reanudable es potencialmente inseguro|
|ADVERTENCIA del compilador (nivel 3) C4423|' STD:: bad_alloc ': lo detectará la clase ('*tipo*') en el *número* de línea|
|ADVERTENCIA del compilador (nivel 3) C4424|catch para '*tipo1*' precedido de '*tipo2*' en el *número*de línea; se puede producir un comportamiento imprevisible si se produce ' STD:: bad_alloc '|
|ADVERTENCIA del compilador (nivel 1) C4425|No se puede aplicar una anotación SAL a '... '|
|ADVERTENCIA del compilador (nivel 1) C4426|las marcas de optimización cambiadas después de incluir el encabezado se pueden deber a #pragma optimizar ()|
|ADVERTENCIA del compilador (nivel 1) C4427|'*operador*': desbordamiento en la división constante, comportamiento no definido|
|[ADVERTENCIA del compilador (nivel 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|posible nombre de carácter universal incompleto o mal formado|
|[ADVERTENCIA del compilador (error) C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|falta el especificador de tipo; se presupone int. Nota: C++no admite default-int|
|[ADVERTENCIA del compilador (nivel 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|falta el especificador de tipo; se presupone int. Nota: C ya no admite default-int|
|[ADVERTENCIA del compilador (nivel 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|un constructor estático debe tener accesibilidad privada; cambiar a acceso privado|
|[ADVERTENCIA del compilador (nivel 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*Derived_Class*': El diseño de objetos en/VD2 cambiará debido a la base virtual '*BASE_CLASS*'|
|[ADVERTENCIA del compilador (nivel 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|la\_conversión dinámica de la base virtual '*BASE_CLASS*' a '*Derived_Class*' en el constructor o destructor podría producir un error con el objeto construido parcialmente|
|[ADVERTENCIA del compilador (nivel 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|error\_en la conversión dinámica de la base virtual '*BASE_CLASS*' a '*Derived_Class*' en algunos contextos|
|ADVERTENCIA del compilador C4438|'*function*': no se puede llamar a de forma segura en el modo/Await: clrcompat. Si '*function*' llama a CLR, puede producir daños en el encabezado de CLR|
|[ADVERTENCIA del compilador (error) C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*función*': la definición de función con un tipo administrado en la signatura debe tener una Convención de llamada _ _ clrcall|
|[ADVERTENCIA del compilador (nivel 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|se ha omitido la nueva definición de la Convención de llamada de '*calling_convention1*' a '*calling_convenction2*'|
|[ADVERTENCIA del compilador (nivel 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|se ha omitido la Convención de llamada de '*calling_convention1*'; se usó '*calling_convention2*' en su lugar|
|ADVERTENCIA del compilador (nivel 1) C4442|terminador null incrustado en el argumento __annotation.  El valor se truncará.|
|ADVERTENCIA del compilador (nivel 1) C4443|se esperaba que el parámetro de pragma fuera ' 0 ', ' 1 ' o ' 2 '|
|ADVERTENCIA del compilador (nivel 3) C4444|'*Identifier*': el nivel superior ' __unaligned ' no está implementado en este contexto|
|[ADVERTENCIA del compilador (nivel 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*función*': en un tipo '&#124;administrado de WinRT ', un método virtual no puede ser privado|
|ADVERTENCIA del compilador (nivel 1) C4446|'*Type*': no se puede asignar el miembro '*nombre1*' a este tipo debido a un conflicto con el nombre de tipo. Se ha cambiado el nombre del método a '*nombre2*'|
|ADVERTENCIA del compilador (nivel 1) C4447|se encontró la signatura ' Main ' sin el modelo de subprocesos. Considere la posibilidad de usar ' int Main (Platform\<:: Array Platform:: String ^ > ^ args) '.|
|ADVERTENCIA del compilador C4448|'*tipo*1 ' no tiene una interfaz predeterminada especificada en los metadatos. Eligiendo: '*tipo2*', que puede producir un error en tiempo de ejecución.|
|ADVERTENCIA del compilador C4449|'*Type*' un tipo no sellado se debe marcar como ' [WebHostHidden] '|
|ADVERTENCIA del compilador C4450|'*tipo1*' se debe marcar como ' [WebHostHidden] ' porque deriva de '*tipo2*'|
|ADVERTENCIA del compilador (nivel 4) C4451|' nombreclase1:: Member ': El uso de la clase ref ' nombreclase2:: Member ' dentro de este contexto puede dar lugar a un cálculo de referencias no válido del objeto en todos los contextos|
|ADVERTENCIA del compilador (nivel 1) C4452|'*Identifier*': el tipo público no puede estar en el ámbito global. Debe estar en un espacio de nombres que sea un elemento secundario del nombre del archivo. winmd de salida.|
|ADVERTENCIA del compilador (nivel 1) C4453|'*tipo*': No se debe usar un tipo ' [WebHostHidden] ' en la superficie publicada de un tipo público que no sea ' [WebHostHidden] '|
|ADVERTENCIA del compilador (nivel 1) C4454|'*function*' está sobrecargada por más del número de parámetros de entrada sin tener especificado [DefaultOverload]. Selección de '*declaration*' como sobrecarga predeterminada|
|ADVERTENCIA del compilador (nivel 1) C4455|' operator *Operator*': los identificadores de sufijo literal que no comienzan por un carácter de subrayado están reservados|
|[Advertencia del compilador (nivel 4) C4456](compiler-warning-level-4-c4456.md)|la declaración de '*Identifier*' oculta la declaración local anterior|
|[Advertencia del compilador (nivel 4) C4457](compiler-warning-level-4-c4457.md)|la declaración de '*Identifier*' oculta el parámetro de función|
|[Advertencia del compilador (nivel 4) C4458](compiler-warning-level-4-c4458.md)|la declaración de '*Identifier*' oculta el miembro de clase|
|[ADVERTENCIA del compilador (nivel 4) C4459](compiler-warning-level-4-c4459.md)|la declaración de '*Identifier*' oculta la declaración global|
|[ADVERTENCIA del compilador (nivel 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|El operador&#124;'*operador*' administrado de WinRT tiene un parámetro pasado por referencia. ' Operador&#124;' administrado por 'WinRT ' tiene una semántica diferente a C++ la del operador '*cpp_operator*'. ¿desea pasar por valor?|
|[ADVERTENCIA del compilador (nivel 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'*className*': esta clase tiene un finalizador '! *finalizador*' pero sin destructor ' ~*Dtor*'|
|[ADVERTENCIA del compilador (nivel 1, error) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*Type*': no se puede determinar el GUID del tipo. El programa puede dar un error en tiempo de ejecución.|
|[ADVERTENCIA del compilador (nivel 4) C4463](compiler-warning-level-4-c4463.md)|desbordamiento asignar '*Value*' a un campo de bits que solo puede contener valores de '*MIN_VALUE*' a '*MAX_VALUE*'|
|[Advertencia del compilador (nivel 4) C4464](../../error-messages/compiler-warnings/c4464.md)|la ruta de acceso de inclusión relativa contiene '.. '|
|[ADVERTENCIA del compilador (nivel 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|pragmas de control de punto flotante omitidas en/CLR|
|[ADVERTENCIA del compilador (nivel 4) C4471](compiler-warning-level-4-c4471.md)|'*enumeración*': una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente (se supone int)|
|ADVERTENCIA del compilador (nivel 1) C4472,|'*Identifier*' es una enumeración nativa: Agregue un especificador de acceso (privado/público) para declarar una enumeración ' WinRT&#124;Managed '|
|[ADVERTENCIA del compilador (nivel 1) C4473](c4473.md)|'*function*': no se pasaron suficientes argumentos para la cadena de formato|
|ADVERTENCIA del compilador (nivel 3) C4474|'*función*': se han pasado demasiados argumentos para la cadena de formato|
|ADVERTENCIA del compilador (nivel 3) C4475|'*función*': el modificador delongitud ' modificador ' no se puede usar con el carácter de campo de tipo '*character*' en el especificador de formato|
|ADVERTENCIA del compilador (nivel 3) C4476|'*función*': carácter de campo de tipo desconocido '*carácter*' en el especificador de formato|
|[ADVERTENCIA del compilador (nivel 1) C4477](c4477.md)|'*función*': la cadena de formato '*cadena*' requiere un argumento de tipo '*tipo*', pero el *número* de argumento de variádicas tiene el tipo '*tipo*'|
|ADVERTENCIA del compilador (nivel 1) C4478|'*función*': los marcadores de posición posicionales y no posicional no se pueden combinar en la misma cadena de formato|
|ADVERTENCIA del compilador (error) C4480|se ha utilizado una extensión no estándar: especificando el tiposubyacente para la enumeración ' enumeración '|
|[ADVERTENCIA del compilador (nivel 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|se ha utilizado una extensión no estándar: especificador de invalidación '*palabra clave*'|
|ADVERTENCIA del compilador C4482|se ha utilizado una extensión no estándar: enumeración ' enumeración ' utilizada en el nombre completo|
|ADVERTENCIA del compilador (nivel 1, error) C4483|error de sintaxis: C++ se esperaba la palabra clave|
|[ADVERTENCIA del compilador (error) C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*override_function*': coincide con el método de clase Ref base '*base_class_function*', pero no está marcado como ' virtual ', ' New ' u ' override '; se presupone ' New ' (y no ' virtual ')|
|[ADVERTENCIA del compilador (error) C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*override_function*': coincide con el método de clase Ref base '*base_class_function*', pero no está marcado como ' New ' u ' override '; se presupone ' New ' (y ' virtual ')|
|[ADVERTENCIA del compilador (nivel 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*función*': un método virtual privado de una clase Ref o una clase de valor se debe marcar como ' Sealed '|
|[ADVERTENCIA del compilador (nivel 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*derived_class_function*': coincide con el método no virtual heredado '*base_class_function*', pero no está marcado explícitamente como ' New '|
|[ADVERTENCIA del compilador (nivel 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*function*': requiere la palabra clave '*Keyword*' para implementar el método de interfaz '*interface_method*'|
|[ADVERTENCIA del compilador (nivel 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*Specifier*': no se permite en el método de interfaz '*Method*'; los especificadores de invalidación solo se permiten en métodos de clase Ref y de clase de valor|
|[ADVERTENCIA del compilador (nivel 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|' override ': uso incorrecto del especificador de invalidación; '*function*' no coincide con un método de clase Ref base|
|ADVERTENCIA del compilador (nivel 1) C4491|'*Name*': tiene un formato de versión IDL no válido|
|ADVERTENCIA del compilador (nivel 1, error) C4492|'*function1*': coincide con el método de clase Ref base '*función2*', pero no está marcado como ' override '|
|ADVERTENCIA del compilador (nivel 3, error) C4493|la expresión delete no tiene efecto porque el destructor de '*Type*' no tiene accesibilidad ' Public '|
|ADVERTENCIA del compilador (nivel 1) C4494|'*función*': Omitir _ _ declspec (allocator) porque el tipo de valor devuelto de la función no es un puntero o una referencia|
|ADVERTENCIA del compilador C4495|se usó la extensión no estándar ' __super ': reemplazar por el nombre de clase base explícito|
|ADVERTENCIA del compilador C4496|se usó la extensión no estándar ' for each ': Reemplace con la instrucción ranged-for|
|ADVERTENCIA del compilador C4497|se usó la extensión no estándar ' Sealed ': reemplace por ' final '|
|ADVERTENCIA del compilador C4498|se ha utilizado una extensión no estándar: '*Extension*'|
|ADVERTENCIA del compilador (nivel 4) C4499|'*función*': una especialización explícita no puede tener una clase de almacenamiento (se omite) "|
|[ADVERTENCIA del compilador (nivel 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'*especificación*de vinculación ' requiere el uso de la palabra clave ' extern ' y debe preceder a todos los demás especificadores|
|[ADVERTENCIA del compilador (nivel 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*Identifier*': se superó la longitud del nombre representativo; el nombre se truncó|
|[ADVERTENCIA del compilador (nivel 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*función*': se ha quitado la función local sin referencia|
|[ADVERTENCIA del compilador (nivel 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|no hay ninguna definición para la función insertada '*function*'|
|[ADVERTENCIA del compilador (nivel 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*función*': la función debe devolver un valor; se supone el tipo de valor devuelto ' void '|
|ADVERTENCIA del compilador C4509|se ha utilizado una extensión no estándar: '*function*' usa SEH y '*Object*' tiene un destructor|
|[ADVERTENCIA del compilador (nivel 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'*Class*': el constructor predeterminado se definió implícitamente como eliminado|
|[ADVERTENCIA del compilador (nivel 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'*Class*': el constructor de copia se definió implícitamente como eliminado|
|[ADVERTENCIA del compilador (nivel 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*Class*': el operador de asignación se definió implícitamente como eliminado|
|[ADVERTENCIA del compilador (nivel 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'*Class*': el destructor se definió implícitamente como eliminado|
|[ADVERTENCIA del compilador (nivel 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*función*': se ha quitado la función insertada a la que no se hace referencia|
|[ADVERTENCIA del compilador (nivel 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*espacio de nombres*': el espacio de nombres se usa a sí mismo|
|[ADVERTENCIA del compilador (nivel 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|' Class:: Symbol ': las declaraciones de acceso están desusadas; las declaraciones Using de miembro proporcionan una mejor alternativa|
|[ADVERTENCIA del compilador (nivel 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|las declaraciones de acceso están desusadas; las declaraciones Using de miembro proporcionan una mejor alternativa|
|[ADVERTENCIA del compilador (nivel 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'*Specifier*': aquí no se esperaban los especificadores de clase o tipo de almacenamiento; tendrán|
|ADVERTENCIA del compilador (error) C4519|los argumentos de plantilla predeterminados solo se permiten en una plantilla de clase|
|[ADVERTENCIA del compilador (nivel 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*Class*': se especificaron varios constructores de copias|
|[ADVERTENCIA del compilador (nivel 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'*Class*': se especificaron varios operadores de asignación|
|[ADVERTENCIA del compilador (nivel 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*Class*': se especificaron varios Destructores|
|[ADVERTENCIA del compilador (nivel 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*función*': la función miembro estática no puede invalidar la invalidación de la función virtual '*virtual function*' omitida; la función virtual se ocultará|
|[ADVERTENCIA del compilador (nivel 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|C++controlador de excepciones usado, pero la semántica de desenredo no está habilitada. Especificar/EHsc|
|ADVERTENCIA del compilador (nivel 1) C4531|C++el control de excepciones no está disponible en Windows CE. Usar el control de excepciones estructurado|
|[ADVERTENCIA del compilador (nivel 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|' Continue ': el salto fuera del bloque ' _ _ Finally/Finally ' tiene un comportamiento indefinido durante el control de finalización|
|[ADVERTENCIA del compilador (nivel 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|'*goto Label*' omite la inicialización de '*variable*'|
|[ADVERTENCIA del compilador (nivel 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'*constructor*' no será un constructor predeterminado para ' Class/struct ' '*Identifier*' debido al argumento predeterminado|
|[ADVERTENCIA del compilador (nivel 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|calling _set_se_translator() requires /EHa|
|[ADVERTENCIA del compilador (nivel 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*TypeName*': el nombre de tipo supera el límite de metadatos de caracteres '*character_limit*'|
|[ADVERTENCIA del compilador (nivel 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*objeto*': '. ' aplicado a un tipo no UDT|
|[ADVERTENCIA del compilador (nivel 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'*Type*': no se admiten calificadores const/volatile en este tipo|
|[ADVERTENCIA del compilador (nivel 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast se usa para convertir a base inaccesible o ambigua; se producirá un error en la prueba en tiempo de ejecución ('*tipo1*' a '*tipo2*')|
|[ADVERTENCIA del compilador (nivel 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'*Identifier*' usado en el tipo polimórfico '*Type*' con/gr-; puede producirse un comportamiento impredecible|
|ADVERTENCIA del compilador (nivel 1) C4542|Omitiendo la generación del archivo de texto insertado combinado; no se puede escribir el archivo *filetype* : '*Issue*': *mensaje*|
|[ADVERTENCIA del compilador (nivel 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|Texto insertado suprimido por el atributo '\_no injected_text '|
|[ADVERTENCIA del compilador (nivel 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'*declaration*': se omitió el argumento de plantilla predeterminado en esta declaración de plantilla|
|[ADVERTENCIA del compilador (nivel 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|la expresión antes de la coma se evalúa como una función a la que le falta una lista de argumentos|
|[ADVERTENCIA del compilador (nivel 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|falta la lista de argumentos de la llamada de función antes de la coma|
|[ADVERTENCIA del compilador (nivel 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*Operator*': el operador antes de la coma no tiene ningún efecto; se esperaba un operador con efectos secundarios|
|[ADVERTENCIA del compilador (nivel 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|la expresión antes de la coma no tiene ningún efecto; se esperaba una expresión con efectos secundarios|
|[ADVERTENCIA del compilador (nivel 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*Operator*': el operador antes de la coma no tiene ningún efecto; ¿deseaba '*operador*'?|
|[ADVERTENCIA del compilador (nivel 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|la expresión se evalúa como una función a la que le falta una lista de argumentos|
|[ADVERTENCIA del compilador (nivel 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|falta la lista de argumentos de la llamada de función|
|[ADVERTENCIA del compilador (nivel 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*Operator*': el operador no tiene ningún efecto; se esperaba un operador con efectos secundarios|
|[ADVERTENCIA del compilador (nivel 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*Operator*': el operador no tiene ningún efecto; ¿ha pensado en el operador?|
|[Advertencia del compilador (nivel 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'*Operator*': Compruebe la prioridad del operador para ver el error posible; usar paréntesis para clarificar la prioridad|
|[ADVERTENCIA del compilador (nivel 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|la expresión no tiene efecto; se esperaba una expresión con efecto secundario|
|[ADVERTENCIA del compilador (nivel 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|el valor del argumento inmediato intrínseco '*Value*' está fuera del intervalo '*lower_bound* - *upper_bound*'|
|[ADVERTENCIA del compilador (nivel 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|' _ _ assume ' contiene el efecto '*efecto*'|
|[ADVERTENCIA del compilador (nivel 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|el valor del operando '*valor*' está fuera del intervalo '*lower_bound* - *upper_bound*'|
|[ADVERTENCIA del compilador (nivel 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*función*': nueva definición; la función obtiene _ _ declspec (modificador)|
|[ADVERTENCIA del compilador (nivel 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|' _ _ fastcall ' es incompatible con la opción '/CLR ': se convierte a ' _ _ Stdcall '|
|ADVERTENCIA del compilador (nivel 4) C4562|se requieren funciones totalmente prototipos con la opción '/CLR ': convirtiendo ' () ' a ' (void) '|
|[ADVERTENCIA del compilador (nivel 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|el método '*Method*' de ' Class ' '*className*' define el parámetro predeterminado no compatible '*Parameter*'|
|[ADVERTENCIA del compilador (nivel 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*función*': nueva definición; el símbolo se declaró previamente con _ _ declspec (modificador)|
|[ADVERTENCIA del compilador (nivel 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|el carácter representado por el nombre de carácter universal '*Char*' no se puede representar en la página de códigos actual (*número*)|
|ADVERTENCIA del compilador (nivel 1) C4568|'*función*': ningún miembro coincide con la signatura de la invalidación explícita|
|ADVERTENCIA del compilador (nivel 3) C4569|'*función*': ningún miembro coincide con la signatura de la invalidación explícita|
|[ADVERTENCIA del compilador (nivel 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'*Type*': no se ha declarado explícitamente como abstracto pero tiene funciones abstractas|
|[ADVERTENCIA del compilador (nivel 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|Información: la semántica de catch (...) cambió desde Visual C++ 7,1; ya no se detectan excepciones estructuradas (SEH)|
|[ADVERTENCIA del compilador (nivel 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|El atributo [ParamArray] está en desuso en/CLR, use '... ' en lugar|
|ADVERTENCIA del compilador (nivel 1) C4573|el uso de '*lambda function*' requiere que el compilador Capture ' this ', pero el modo de captura predeterminado actual no lo permite|
|ADVERTENCIA del compilador (nivel 4) C4574|'*Identifier*' está definido como ' 0 ': ¿pretendía usar ' #if identificador '?|
|ADVERTENCIA del compilador (nivel 1) C4575|' __vectorcall ' es incompatible con la opción '/CLR ': se convierte a ' _ _ Stdcall '|
|ADVERTENCIA del compilador (nivel 1, error) C4576|un tipo entre paréntesis seguido de una lista de inicializadores es una sintaxis de conversión de tipos explícita no estándar|
|ADVERTENCIA del compilador (nivel 1, OFF) C4577|' Except ' se usa sin el modo de control de excepciones especificado; no se garantiza la terminación en la excepción. Especificar/EHsc|
|ADVERTENCIA del compilador (nivel 1, error) C4578|' ABS ': conversión de '*tipo1*' a '*tipo2*', posible pérdida de datos (¿quiso llamar a '*function*' o #include \<CMATH >?)|
|[ADVERTENCIA del compilador (nivel 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] está desusado; especifique en su lugar System::Attribute o Platform::Metadata como clase base|
|[ADVERTENCIA del compilador (nivel 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|comportamiento en desuso: ' "*cadena*" ' se ha reemplazado por '*cadena*' para procesar el atributo|
|ADVERTENCIA del compilador (nivel 4) C4582|'*Type*': no se llama implícitamente al constructor|
|ADVERTENCIA del compilador (nivel 4) C4583|'*Type*': no se llama implícitamente al destructor|
|[ADVERTENCIA del compilador (nivel 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*Class1*': la clase base '*clase2*' ya es una clase base de '*class3*'|
|ADVERTENCIA del compilador (nivel 1, error) C4585|'*clase*': Una clase Ref pública de WinRT debe estar sellada o derivar de una clase no sellada existente.|
|ADVERTENCIA del compilador (nivel 1, error) C4586|'*tipo*': Un tipo público no se puede declarar en un espacio de nombres de nivel superior denominado ' Windows '|
|ADVERTENCIA del compilador (nivel 1) C4587|'*anonymous_structure*': cambio de comportamiento: ya no se llama implícitamente al constructor|
|ADVERTENCIA del compilador (nivel 1) C4588|'*anonymous_structure*': cambio de comportamiento: ya no se llama implícitamente al destructor|
|ADVERTENCIA del compilador (nivel 1) C4591|se superó el límite de profundidad de llamadas de ' constexpr ' (\</constexpr: número de profundidad >)|
|ADVERTENCIA del compilador (nivel 3) C4592|'*función*': error en la evaluación de la llamada ' constexpr '; se llamará a la función en tiempo de ejecución|
|ADVERTENCIA del compilador (nivel 1) C4593|'*función*': se ha superado el límite de paso de evaluación de llamada ' constexpr ' de '*Limit*'; Use/constexpr: Steps\<Number > para aumentar el límite|
|ADVERTENCIA del compilador (nivel 3) C4594|'*Type*': no se llamará implícitamente al destructor si se produce una excepción|
|ADVERTENCIA del compilador (nivel 1) C4595|'*Type*': cambio de comportamiento: ya no se llamará implícitamente al destructor si se produce una excepción|
|[ADVERTENCIA del compilador (nivel 4) C4596](../../error-messages/compiler-warnings/c4596.md)|'*Identifier*': nombre completo no válido en la declaración de miembro|
|ADVERTENCIA del compilador (error) C4597|comportamiento no definido: PosiciónInicial aplicado a un miembro de una base virtual|
|ADVERTENCIA del compilador (nivel 1 y nivel 3) C4598|' #include '*encabezado*' ': el *número* de encabezado del encabezado precompilado no coincide con la compilación actual en esa posición|
|ADVERTENCIA del compilador (nivel 3) C4599|' *ruta de acceso*de marca ': el *número* de argumento de la línea de comandos no coincide con el encabezado precompilado|

## <a name="see-also"></a>Vea también

[Errores yC++ advertencias de las herramientas de compilación y el compilador de C/](../compiler-errors-1/c-cpp-build-errors.md) \
[Advertencias del compilador C4000-C5999](compiler-warnings-c4000-c5999.md)
