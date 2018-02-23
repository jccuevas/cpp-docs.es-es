---
title: "Las advertencias del compilador que están desactivadas de forma predeterminada | Documentos de Microsoft"
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca1fdff6f5be88d7562f1735ea31323ca5a70360
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2018
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Advertencias del compilador que están desactivadas de forma predeterminada

El compilador incluye advertencias que están desactivadas de forma predeterminada, porque la mayoría de los desarrolladores no desea verlos. En algunos casos, representa una opción de estilo, son expresiones comunes en código antiguo o aprovechar las ventajas de una extensión de Microsoft del lenguaje. En otros casos, indican un área donde los programadores a menudo no hacen suposiciones válidas, lo que pueden provocar un comportamiento inesperado o no definido. Algunas de estas advertencias pueden ser con mucho ruido en los encabezados de la biblioteca.

Puede habilitar estas advertencias mediante una de las siguientes opciones:

- **#pragma warning (valor predeterminado:** *warning_number* **)**  
   La advertencia especificada (*warning_number*) está habilitada en su nivel predeterminado. La documentación de la advertencia contiene el nivel predeterminado de la advertencia.

- **#pragma warning (** *nivel_advertencia* **:** *warning_number* **)**  
   La advertencia especificada (*warning_number*) está habilitada en el nivel especificado (*nivel_advertencia*).

- [/Wall](../build/reference/compiler-option-warning-level.md)  
   **/ Pared** habilita todas las advertencias que están desactivadas de forma predeterminada. Si utiliza esta opción, puede desactivar las advertencias individuales mediante la [/wd](../build/reference/compiler-option-warning-level.md) opción.

- [/w*lnnnn*](../build/reference/compiler-option-warning-level.md)  
   Esto habilita la advertencia  *nnnn*  en nivel *l*.

Las siguientes advertencias están deshabilitadas de forma predeterminada.

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (nivel 4)|enumerador '*identificador*'en una instrucción switch de la enumeración'*enumeración*' no está controlada de forma explícita por una etiqueta de caso|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (nivel 4)|enumerador '*identificador*'en una instrucción switch de la enumeración'*enumeración*' no está controlado|
|C4191 (nivel 3)|'*operador*': conversión no segura de '*type_of_expression*'to'*type_required*'|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (nivel 4)|'*identificador*': conversión de '*type1*'to'*type2*', posible pérdida de datos|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (nivel 4)|'*operador*': conversión de '*type1*'to'*type2*', posible pérdida de datos|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (nivel 4)|'*función*': no se ha proporcionado un prototipo de función: convirtiendo '()' a '(void)'|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (nivel 4)|'*función*': función miembro no reemplaza ninguna función miembro virtual de clase base|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (nivel 1)|'*función_virtual*': no hay un reemplazo disponible para la función miembro virtual de base '*clase*'; se oculta la función|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (nivel 3)|'*clase*': clase tiene funciones virtuales, pero el destructor no es virtual|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (nivel 4)|'*función*': no hay un reemplazo disponible para la función miembro virtual de base '*tipo*'; se oculta la función|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (nivel 3)|'*operador*': no coinciden las constantes sin signo o negativas|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (nivel 4)|ha utilizado una extensión no estándar: '*var*': variable de control de bucles declarada en el bucle for se utiliza fuera del ámbito del bucle for|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (nivel 4)|'*operador*': expresión siempre es false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (nivel 4)|'*tipo*': detectó el uso de un tipo no definido en los metadatos CLR - uso de este tipo puede provocar una excepción en tiempo de ejecución|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (nivel 1)|cambio de comportamiento: '*función*' llama, pero en versiones anteriores se llamaba a un operador de miembro|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (nivel 1)|cambio de comportamiento: '*member1*'que se llama en lugar de'*member2*'|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this': utilizado en la lista de inicializadores de miembro base|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (nivel 4)|'*acción*': conversión de '*type_1*'to'*type_2*', no coinciden signed/unsigned|
|C4370 (nivel 3)|el diseño de clase cambió desde una versión anterior del compilador debido a una mejora del empaquetado|
|[C4371](../error-messages/compiler-warnings/c4371.md) (nivel 3)|'*classname*': el diseño de clase puede haber cambiado desde una versión anterior del compilador debido a una mejora del empaquetado del miembro '*miembro*'|
|C4388 (nivel 4)|no coinciden signed/unsigned|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (nivel 2)|'*función*': función firma contiene el tipo '*tipo*'; Objetos de C++ son no es seguro pasar entre código puro y mixto o nativo|
|C4426 (nivel 1)|marcas de optimización cambiadas después de incluir el encabezado, se puede deber a #pragma optimize()|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (nivel 4)|'*class1*': disposición de los objetos en/vd2 cambiará debido a la base virtual '*clase2*'|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (nivel 4)|dynamic_cast de base virtual '*class1*'to'*clase2*' podría producirse un error en algunos contextos|
|C4444 (nivel 3)|el nivel superior '__unaligned' no está implementado en este contexto|
|C4464 (nivel 4)|ruta de acceso de inclusión relativa contiene '..'|
|C4472 (nivel 1)|'*identificador*' es una enumeración nativa: agregue un especificador de acceso (público/privado) para declarar una enumeración administrada|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (nivel 4)|'*función*': se ha quitado la función inline no referenciada|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (nivel 4)|'type name': nombre de tipo supera el límite de metadatos de '*límite*' caracteres|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (nivel 1)|la expresión antes de la coma se evalúa como una función a la que le falta una lista de argumentos|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (nivel 1)|falta la lista de argumentos de la llamada de función antes de la coma|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (nivel 1)|'*operador*': operador antes de una coma no tiene ningún efecto; se esperaba un operador con efectos secundarios|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (nivel 1)|la expresión antes de la coma no tiene ningún efecto; se esperaba una expresión con efectos secundarios|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (nivel 1)|'*operator1*': operador antes de la coma no tiene ningún efecto; ¿deseaba '*operator2*'?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (nivel 1)|la expresión no tiene efecto; se esperaba una expresión con efecto secundario|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (nivel 3)|'__assume' contiene el efecto '*efecto*'|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (nivel 4)|Informativo: la semántica de catch cambiada desde Visual C++ 7.1; ya no se detectan excepciones estructuradas (SEH)|
|C4574 (nivel 4)|'*identificador*'se define como ' 0': ¿pretendía usar ' #if *identificador*'?|
|C4582 (nivel 4)|'*tipo*': no se llama implícitamente a constructor|
|C4583 (nivel 4)|'*tipo*': no se llama implícitamente a destructores|
|C4587 (nivel 1)|'*anonymous_structure*': cambio de comportamiento: constructor implícitamente ya no se llama|
|C4588 (nivel 1)|'*anonymous_structure*': cambio de comportamiento: destructor implícitamente ya no se llama|
|C4598 (nivel 1 y nivel 3)|' #include "*encabezado*"': número de encabezado *número* en el encabezado precompilado no coincide con la compilación actual en esa posición|
|C4599 (nivel 3)|'*opción* *ruta de acceso*': número de argumento de línea de comandos *número* no coincide con el encabezado precompilado|
|C4605 (nivel 1)|' /D*macro*' especificado en la línea de comandos actual, pero no se especificó cuando se creó el encabezado precompilado|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (nivel 3)|#pragma warning: no hay ningún número de advertencia '*número*'|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (nivel 4)|'clase derivada': no se puede generar el constructor predeterminado porque no se puede obtener acceso a un constructor predeterminado de clase base|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (nivel 4)|'clase derivada': no se puede generar el constructor de copias porque no se puede obtener acceso a un constructor de copias de clase base|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (nivel 4)|'clase derivada': no se puede generar el operador de asignaciones porque no se puede obtener acceso a un operador de asignaciones de clase base|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (nivel 1)|los digramas no son compatibles con -Ze. Secuencia de caracteres '*digrama*'no interpretado como token alternativo de'*char*'|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (nivel 3)|'*instancia*': la construcción del objeto estático local no es segura para subprocesos|
|C4647 (nivel 3)|cambio de comportamiento: __is_pod (*tipo*) tiene un valor diferente en las versiones anteriores|
|C4654 (nivel 4)|Incluir código se coloca antes del encabezado precompilado se pasará por alto de línea. Agregue código al encabezado precompilado.|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (nivel 4)|'*símbolo*'no está definido como macro de preprocesador y se reemplaza por '0' para'*directivas*'|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (nivel 4)|'*símbolo*': parámetro direccional se especificó ningún atributo, el valor predeterminado [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (nivel 3)|'*tipo definido por el usuario*': posible cambio de comportamiento, cambio de UDT devuelta de convención de llamada|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (nivel 1)|'*función*': firma de un miembro no privado contiene el tipo nativo privado de ensamblado '*tipo_nativo*'|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (nivel 4)|'*función*': función no está entre línea|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (nivel 3)|almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|acceso volátil de '*expresión*' está sujeta a /volatile:\<iso &#124; ms > establecer; considere el uso de funciones intrínsecas de __iso_volatile_load/almacén|
|C4749 (nivel 4)|admite condicionalmente: offsetof aplicado al tipo de diseño de standard sin '*tipo*'|
|C4767 (nivel 4)|nombre de sección '*símbolo*' tiene más de 8 caracteres y se truncará el vinculador|
|C4768 (nivel 3)|se omiten los atributos __declspec antes de la especificación de vinculación|
|C4774 (nivel 4)|'*cadena*': se esperaba en un argumento de una cadena de formato *número* no es literal de cadena|
|C4786 (nivel 3)|'*símbolo*': nombre de objeto se ha truncado a '*número*' caracteres en la información de depuración|
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (nivel 4)|'*bytes*'bytes de relleno agregados después de construcción'*member_name*'|
|C4826 (nivel 2)|Conversión de '*type1*'to'*type2*' es la extensión de signo. Esto puede provocar un comportamiento inesperado en tiempo de ejecución.|
|C4837 (nivel 4)|se detectó un trígrafo: '?? *caracteres*'reemplazado por'*caracteres*'|
|C4841 (nivel 4)|ha utilizado una extensión no estándar: designador de miembro compuesta utilizado en offsetof|
|C4842 (nivel 4)|el resultado de 'offsetof' aplicado a un tipo mediante herencia múltiple no se garantiza que sea coherente entre las versiones del compilador|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (nivel 4)|'_archivo_(*line_number*)' compilador no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicialización entre llaves|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (nivel 1)|conversión de literal de cadena de tipo ancho a 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (nivel 1)|conversión de literal de cadena a 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (nivel 1)|'*declarador*': un GUID solo puede asociarse con una clase, interfaz o espacio de nombres|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (nivel 1)|inicialización de copia no válida; se aplicó implícitamente más de una conversión definida por el usuario|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (nivel 4)|se supone que la biblioteca de tipos se compiló para punteros de (número) bits|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (nivel 1)|se utilizó reinterpret_cast entre clases relacionadas: '*class1*'y'*clase2*'|
|C4962|'*función*': las optimizaciones guiadas por perfil deshabilitadas porque generaban datos de perfil incoherentes|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (nivel 4)|'*símbolo*': especificación de excepción no coincide con la declaración anterior.|
|C4987 (nivel 4)|se usó una extensión no estándar: 'throw (...)'|
|C4988 (nivel 4)|'*símbolo*': variable declarada fuera ámbito de clase o función|
|C5022|'*tipo*': han especificado varios constructores de movimiento|
|C5023|'*tipo*': varios operadores de asignación de movimiento especificados|
|C5024 (nivel 4)|'*tipo*': mover constructor se definió implícitamente como eliminado|
|C5025 (nivel 4)|'*tipo*': mover operador de asignación se definió implícitamente como eliminado|
|C5026 (nivel 1 y nivel 4)|'*tipo*': mover constructor se definió implícitamente como eliminado|
|C5027 (nivel 1 y nivel 4)|'*tipo*': mover operador de asignación se definió implícitamente como eliminado|
|C5029 (nivel 4)|ha utilizado una extensión no estándar: atributos de alineación en C++ que se aplican a las variables, los miembros de datos y solo los tipos de etiquetas|
|C5031 (nivel 4)|#pragma warning (POP): probablemente falta de coincidencia, retirar el estado de advertencia insertado en otro archivo|
|C5032 (nivel 4)|detectado #pragma warning (Push) con ningún Warning (POP) #pragma correspondiente|
|C5035|el uso de la característica '*característica*' hace función *función* se compile como código de invitado|
|C5036 (nivel 1)|varargs función de conversión de puntero cuando se compila con /hybrid:x86arm64 '*type1*'to'*type2*'|
|[C5038](../error-messages/compiler-warnings/c5038.md)|miembro de datos '*member1*'se inicializará después del miembro de datos'*member2*'|

Estas advertencias están desactivadas, a menos que la [/ permisivo-](../build/reference/permissive-standards-conformance.md) se establece la opción del compilador:

|||
|-|-|
|[C4471 (nivel 4)](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md)|una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente (se presupone int)|
|[C4608 (nivel 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'*union_member*'ya se ha inicializado por otro miembro union en la lista de inicializadores,'*union_member*'|

Estas advertencias eran desactivado de forma predeterminada en las versiones del compilador antes de Visual Studio 2015:

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (nivel 2)|'*conversión*': truncamiento de '*type1*'to'*type2*'|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (nivel 1)|'*variable*': truncamiento de puntero de '*tipo*'to'*tipo*'|
|[El error C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (nivel 1)|'*operación*': conversión de '*type1*'to'*type2*' de mayor tamaño|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (nivel 1)|'*operador*': extensión de cero '*type1*'to'*type2*' de mayor tamaño|

Estas advertencias eran desactivado de forma predeterminada en las versiones del compilador antes de Visual Studio 2012:

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (nivel 4)|falta el especificador de tipo; se presupone int. Nota: C no admite default-int|

## <a name="see-also"></a>Vea también

[warning](../preprocessor/warning.md)
