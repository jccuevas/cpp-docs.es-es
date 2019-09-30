---
title: Advertencias del compilador desactivadas de forma predeterminada
ms.date: 08/29/2019
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: ac6ad3b5bbe5f3a738dc0019a43ff08a17cf27ca
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685715"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Advertencias del compilador desactivadas de forma predeterminada

El compilador admite advertencias que están desactivadas de forma predeterminada, ya que la mayoría de los desarrolladores no las encuentran útiles. En algunos casos, avisan sobre una elección de estilo o sobre expresiones comunes en código antiguo. Otras advertencias son sobre el uso de una extensión de Microsoft para el lenguaje. Algunas advertencias indican un área en la que los programadores a menudo realizan suposiciones incorrectas, lo que puede provocar un comportamiento inesperado o indefinido. Si todas estas advertencias están habilitadas, algunas de ellas pueden aparecer muchas veces en encabezados de biblioteca. Las bibliotecas en tiempo de ejecución C++ de C y las bibliotecas estándar están diseñadas para no emitir ninguna advertencia solo en el nivel de advertencia [/W4](../build/reference/compiler-option-warning-level.md).

## <a name="enable-warnings-that-are-off-by-default"></a>Habilitar advertencias que están desactivadas de forma predeterminada

Puede habilitar las advertencias que normalmente están desactivadas de forma predeterminada mediante una de las siguientes opciones:

- **#pragma ADVERTENCIA (valor predeterminado:** *warning_number* **)**

   La advertencia especificada (*warning_number*) está habilitada en su nivel predeterminado. La documentación de la advertencia contiene el nivel predeterminado de la advertencia.

- **ADVERTENCIA #pragma (** *warning_level* **:** *warning_number* **)**

   La advertencia especificada (*warning_number*) está habilitada en el nivel especificado (*warning_level*).

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall` habilita todas las advertencias que están desactivadas de forma predeterminada. Si utiliza esta opción, puede desactivar las advertencias individuales mediante la opción [/WD](../build/reference/compiler-option-warning-level.md) .

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   Esta opción habilita la advertencia *nnnn* en el nivel *L*.

## <a name="warnings-that-are-off-by-default"></a>Advertencias que están desactivadas de forma predeterminada

Las siguientes advertencias están desactivadas de forma predeterminada en Visual Studio 2015 y versiones posteriores:

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (nivel 4)|un enumerador '*Identifier*' en un modificador de la enumeración '*enumeración*' no está controlado explícitamente por una etiqueta de caso|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (nivel 4)|el enumerador '*Identifier*' de un modificador de la enumeración '*enumeración*' no está controlado|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md) (nivel 1) | ' HRESULT ' se está convirtiendo en ' bool '; ¿está seguro de que es lo que desea? |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md) (nivel 3)|'*operador*': conversión no segura de '*type_of_expression*' a '*type_required*'|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (nivel 4)|'*Identifier*': conversión de '*tipo1*' a '*tipo2*', posible pérdida de datos|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (nivel 4)|'*operador*': conversión de '*tipo1*' a '*tipo2*', posible pérdida de datos|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (nivel 4)|'*función*': no se ha proporcionado ningún prototipo de función: convirtiendo ' () ' a ' (void) '|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (nivel 4)|'*función*': la función miembro no invalida ninguna función miembro virtual de clase base|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (nivel 1)|'*virtual_function*': no hay ningún reemplazo disponible para la función miembro virtual de la base '*Class*'. la función está oculta|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (nivel 3)|'*Class*': la clase tiene funciones virtuales, pero el destructor no es virtual|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (nivel 4)|'*función*': no hay ningún reemplazo disponible para la función miembro virtual de '*tipo*' base; la función está oculta|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (nivel 3)|'*operador*': no coinciden las constantes sin signo o negativas|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (nivel 4)|se ha utilizado una extensión no estándar: '*var*': la variable de control de bucles declarada en el bucle for se utiliza fuera del ámbito del bucle for|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (nivel 4)|'*Operator*': la expresión siempre es false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (nivel 4)|'*Type*': se detectó el uso de un tipo no definido en los metadatos de CLR; el uso de este tipo puede provocar una excepción en tiempo de ejecución|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (nivel 1)|cambio de comportamiento: se llamó a '*función*', pero se llamó a un operador de miembro en versiones anteriores|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (nivel 1)|cambio de comportamiento: se llamó a '*member1*' en lugar de a '*miembro2*'|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this': utilizado en la lista de inicializadores de miembro base|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (nivel 4)|'*Action*': conversión de '*TYPE_1*' a '*TYPE_2*', no coincide con signed/unsigned|
|C4370 (nivel 3)|el diseño de clase cambió desde una versión anterior del compilador debido a una mejora del empaquetado|
|[C4371](../error-messages/compiler-warnings/c4371.md) (nivel 3)|'*className*': el diseño de clase puede haber cambiado desde una versión anterior del compilador debido a una mejora del empaquetado del miembro '*miembro*'|
|C4388 (nivel 4)|no coinciden signed/unsigned|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (nivel 2)|'*función*': la firma de la función contiene el tipo '*tipo*'; C++ los objetos no son seguros para pasar entre código puro y mixto o nativo|
|C4426 (nivel 1)|las marcas de optimización cambiadas después de incluir el encabezado puede ser debido a #pragma Optimize () <sup>14,1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (nivel 4)|'*Class1*': El diseño de objetos en/VD2 cambiará debido a la base de datos virtual '*clase2*'|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (nivel 4)|error de dynamic_cast de la base virtual '*Class1*' a '*clase2*' en algunos contextos|
|C4444 (nivel 3)|el nivel superior '__unaligned' no está implementado en este contexto|
|[C4464](../error-messages/compiler-warnings/c4464.md) (nivel 4)|la ruta de acceso de inclusión relativa contiene '.. '|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (nivel 4)|una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente (se supone int) <sup>Perm</sup>|
|C4472, (nivel 1)|'*Identifier*' es una enumeración nativa: Agregue un especificador de acceso (privado/público) para declarar una enumeración administrada|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (nivel 4)|'*función*': se ha quitado la función insertada a la que no se hace referencia|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (nivel 4)|' nombre de tipo ': el nombre de tipo supera el límite de metadatos de '*Limit*' caracteres|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (nivel 1)|la expresión antes de la coma se evalúa como una función a la que le falta una lista de argumentos|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (nivel 1)|falta la lista de argumentos de la llamada de función antes de la coma|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (nivel 1)|'*Operator*': el operador antes de la coma no tiene ningún efecto; se esperaba un operador con efectos secundarios|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (nivel 1)|la expresión antes de la coma no tiene ningún efecto; se esperaba una expresión con efectos secundarios|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (nivel 1)|'*operator1*': el operador antes de la coma no tiene ningún efecto; ¿deseaba '*operator2*'?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (nivel 1)|la expresión no tiene efecto; se esperaba una expresión con efecto secundario|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (nivel 3)|' _ _ assume ' contiene el efecto '*efecto*'|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (nivel 4)|información: la semántica de catch (...) cambió desde Visual C++ 7,1; ya no se detectan excepciones estructuradas (SEH)|
|C4574 (nivel 4)|'*Identifier*' está definido como ' 0 ': ¿pretendía usar ' #if *identificador*'?|
|C4577 (nivel 1)|' Except ' se usa sin el modo de control de excepciones especificado; no se garantiza la terminación en la excepción. Especificar/EHsc|
|C4582 (nivel 4)|'*Type*': no se llama implícitamente al constructor|
|C4583 (nivel 4)|'*Type*': no se llama implícitamente al destructor|
|C4587 (nivel 1)|'*anonymous_structure*': cambio de comportamiento: ya no se llama implícitamente al constructor|
|C4588 (nivel 1)|'*anonymous_structure*': cambio de comportamiento: ya no se llama implícitamente al destructor|
|[C4596](../error-messages/compiler-warnings/c4596.md) (nivel 4)|'*Identifier*': nombre completo no válido en la declaración de miembro <sup>14,3</sup> <sup>Perm</sup>|
|C4598 (nivel 1 y nivel 3)|' #include '*encabezado*' ': el encabezado del número de encabezado *-número* en el encabezado precompilado no coincide con la compilación actual en esa posición <sup>14,3</sup>|
|C4599 (nivel 3)|'*Option* *path*': *el número de* argumento de la línea de comandos no coincide con el encabezado precompilado <sup>14,3</sup>|
|C4605 (nivel 1)|'/D*macro*' especificada en la línea de comandos actual, pero no se especificó cuando se compiló el encabezado precompilado|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (nivel 3)|'*union_member*' ya ha sido inicializado por otro miembro Union en la lista de inicializadores, '*union_member*' <sup>Perm</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (nivel 3)|#pragma ADVERTENCIA: no hay ningún número de advertencia '*número*'|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (nivel 4)|'clase derivada': no se puede generar el constructor predeterminado porque no se puede obtener acceso a un constructor predeterminado de clase base|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (nivel 4)|'clase derivada': no se puede generar el constructor de copias porque no se puede obtener acceso a un constructor de copias de clase base|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (nivel 4)|'clase derivada': no se puede generar el operador de asignaciones porque no se puede obtener acceso a un operador de asignaciones de clase base|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (nivel 1)|los digramas no son compatibles con -Ze. La secuencia de caracteres '*dígrafo*' no se interpreta como token alternativo para '*Char*'|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (nivel 3)|'*Instance*': la construcción del objeto estático local no es segura para subprocesos|
| C4643 (nivel 4) | La declaración adelantada '*Identifier*' en el espacio de nombres STD no está C++ permitida por el estándar. <sup>15.8</sup> |
|C4647 (nivel 3)|cambio de comportamiento: __is_pod (*tipo*) tiene un valor diferente en las versiones anteriores|
|C4654 (nivel 4)|Se omitirá el código colocado antes de incluir la línea del encabezado precompilado. Agregue código al encabezado precompilado. <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (nivel 4)|'*Symbol*' no está definido como una macro de preprocesador y se reemplaza por ' 0 ' para '*directives*'|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (nivel 4)|'*Symbol*': no se especificó ningún atributo de parámetro direccional; el valor predeterminado es [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (nivel 3)|'*tipo definido por el usuario*': posible cambio de comportamiento, cambio en la Convención de llamada de devolución UDT|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (nivel 1)|'*función*': la signatura de un miembro no privado contiene un tipo nativo privado de ensamblado '*native_type*'|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (nivel 4)|'*función*': la función no está insertada|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (nivel 3)|almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|el acceso volátil de '*Expression*' está sujeto a la opción/volatile:&#124;\<ISO MS >. considerar el uso de funciones intrínsecas de __iso_volatile_load/Store|
|C4749 (nivel 4)|compatibilidad condicional: desplazamiento aplicado al tipo de diseño no estándar '*tipo*'|
|C4767 (nivel 4)|el nombre de sección '*Symbol*' tiene más de 8 caracteres y lo truncará el vinculador|
|C4768 (nivel 3)|se omiten los atributos _ _ declspec antes de la especificación de vinculación|
|C4774 (nivel 4)|'*cadena*': la cadena de formato esperada en el *número* de argumento no es un literal de cadena|
|C4777 (nivel 4)|'*función*': la cadena de formato '*cadena*' requiere un argumento de tipo '*tipo1*', pero el *número* de argumento de variádicas tiene el tipo '*tipo2*'|
|C4786 (nivel 3)|'*Symbol*': el nombre del objeto se truncó en '*número*' caracteres en la información de depuración|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) (nivel 4) | Conversión implícita de '*tipo*' a bool. Posible pérdida de información <sup>16,0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (nivel 4)|'*bytes*' bytes de relleno agregados después de la construcción '*member_name*'|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md) (nivel 1) | '*member*': la función miembro de clase local no tiene cuerpo |
|C4826 (nivel 2)|La conversión de '*tipo1*' a '*tipo2*' tiene signo. Esto puede producir un comportamiento inesperado en tiempo de ejecución.|
|C4837 (nivel 4)|se detectó un trígrafo: '?? *carácter*' reemplazado por '*carácter*'|
|C4841 (nivel 4)|se ha utilizado una extensión no estándar: designador de miembro compuesto usado en DESREF|
|C4842 (nivel 4)|no se garantiza que el resultado de ' offsetto ' aplicado a un tipo mediante herencia múltiple sea coherente entre versiones del compilador|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (nivel 4)|el compilador '_File_(*line_number*) ' no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicialización entre llaves|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (nivel 1)|conversión de literal de cadena de tipo ancho a 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (nivel 1)|conversión de literal de cadena a 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (nivel 1)|'*declarador*': un GUID solo se puede asociar a una clase, interfaz o espacio de nombres|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (nivel 1)|inicialización de copia no válida; se aplicó implícitamente más de una conversión definida por el usuario|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (nivel 4)|se supone que la biblioteca de tipos se compiló para punteros de (número) bits|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (nivel 1)|se utilizó reinterpret_cast entre clases relacionadas: '*Class1*' y '*clase2*'|
|C4962|'*función*': se han deshabilitado las optimizaciones guiadas por perfiles porque las optimizaciones produjeron datos de perfil incoherentes|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (nivel 4)|'*Symbol*': la especificación de la excepción no coincide con la declaración anterior|
|C4987 (nivel 4)|se usó una extensión no estándar: 'throw (...)'|
|C4988 (nivel 4)|'*Symbol*': variable declarada fuera del ámbito de clase o función|
|C5022|'*Type*': se especificaron varios constructores de movimiento|
|C5023|'*Type*': se especificaron varios operadores de asignación de movimiento|
|C5024 (nivel 4)|'*Type*': el constructor de movimiento se definió implícitamente como eliminado|
|C5025 (nivel 4)|'*Type*': el operador de asignación de movimiento se definió implícitamente como eliminado|
|C5026 (nivel 1 y nivel 4)|'*Type*': el constructor de movimiento se definió implícitamente como eliminado|
|C5027 (nivel 1 y nivel 4)|'*Type*': el operador de asignación de movimiento se definió implícitamente como eliminado|
|C5029 (nivel 4)|se ha utilizado una extensión no estándar: C++ los atributos de alineación de solo se aplican a variables, miembros de datos y tipos de etiqueta|
|C5031 (nivel 4)|ADVERTENCIA de #pragma (pop): probable falta de coincidencia, se insertó el estado de advertencia insertado en el archivo diferente <sup>14,1</sup>|
|C5032 (nivel 4)|se detectó #pragma ADVERTENCIA (inserciones) sin la advertencia #pragma correspondiente (pop) <sup>14,1</sup>|
|C5034|el uso de '*Intrinsic*' intrínseco hace que *el nombre de función-* función se compile como código de invitado <sup>15,3</sup>|
|C5035|el uso de la característica '*Feature*' hace que *el nombre de función-* función se compile como código de invitado <sup>15,3</sup>|
|C5036 (nivel 1)|conversión del puntero de función varargs al compilar con/Hybrid: x86arm64 '*Type1*' en '*Type2*' <sup>15,3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) (nivel 4)|el miembro de datos '*member1*' se inicializará después del miembro de datos '*miembro2*' <sup>15,3</sup>|
|C5039 (nivel 4)|'*function*': puntero o referencia a una función de inicio que se pasa a la función extern C en-EHC. Se puede producir un comportamiento indefinido si esta función produce una excepción. <sup>15,5</sup>|
|C5042 (nivel 3)|'*función*': las declaraciones de función en el ámbito de bloque no se pueden especificar como ' C++inline ' en el estándar; quitar el especificador "inline" <sup>15,5</sup>|
|[C5045](../error-messages/compiler-warnings/c5045.md)|El compilador insertará la mitigación de Spectre para la carga de memoria si se especifica el modificador/Qspectre <sup>15,7</sup>|

<sup>14,1</sup> esta advertencia está disponible a partir de Visual Studio 2015 Update 1. <br/>
<sup>14,3</sup> esta advertencia está disponible a partir de Visual Studio 2015 Update 3. <br/>
<sup>15,3</sup> esta advertencia está disponible a partir de la versión 15,3 de Visual Studio 2017. <br/>
<sup>15,5</sup> esta advertencia está disponible a partir de la versión 15,5 de Visual Studio 2017. <br/>
<sup>15,7</sup> esta advertencia está disponible a partir de la versión 15,7 de Visual Studio 2017. <br/>
<sup>15,8</sup> esta advertencia está disponible a partir de la versión 15,8 de Visual Studio 2017. <br/>
<sup>16,0</sup> esta advertencia está disponible a partir de Visual Studio 2019 RTM. <br/>
<sup>Perm</sup> Esta advertencia está desactivada a menos que se establezca la opción del compilador [/permissive-](../build/reference/permissive-standards-conformance.md)

## <a name="warnings-off-by-default-in-earlier-versions"></a>ADVERTENCIAS desactivadas de forma predeterminada en versiones anteriores

Estas advertencias estaban desactivadas de forma predeterminada en las versiones del compilador antes de Visual Studio 2015:

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (nivel 2)|'*Conversion*': truncamiento de '*tipo1*' a '*tipo2*'|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (nivel 1)|'*variable*': truncamiento de puntero de '*tipo*' a '*tipo*'|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (nivel 1)|'*Operation*': conversión de '*tipo1*' a '*tipo2*' de mayor tamaño|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (nivel 1)|'*operador*': extensión de cero de '*tipo1*' a '*tipo2*' de mayor tamaño|

Esta advertencia estaba desactivada de forma predeterminada en las versiones del compilador antes de Visual Studio 2012:

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (nivel 4)|falta el especificador de tipo; se presupone int. Nota: C ya no admite default-int|

## <a name="see-also"></a>Vea también

[warning](../preprocessor/warning.md)
