---
title: Advertencias del compilador por versión del compilador | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- devlang-cpp
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- warnings, by compiler version
- cl.exe compiler, setting warning options
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4d815ba1036a03042992d2715e49bbd8f74a28
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990391"
---
# <a name="compiler-warnings-by-compiler-version"></a>Advertencias del compilador por versión del compilador

El compilador puede suprimir las advertencias que se introdujeron después de una versión se especifica mediante el [/wv](../../build/reference/compiler-option-warning-level.md) opción del compilador. Esto es útil para administrar el proceso de compilación al introducir una nueva versión del conjunto de herramientas y desea suprimir temporalmente nuevas advertencias. Esta opción no suprime los mensajes de error. No se recomienda suprimir todas las advertencias nuevas permanentemente! Se recomienda que siempre se compila en el nivel más alto de la advertencia regular, __/W4__y quite el __/wv__ opción tan pronto como sea posible en la compilación.

Estas versiones del compilador introdujeron nuevas advertencias:

| Producto | Número de versión del compilador |
|-|-|
| Visual C++ 2002 | 13.00.9466 |
| Visual C++ 2003 | 13.10.3077 |
| Visual C++ 2005 | 14.00.50727.762 |
| Visual C++ 2008 | 15.00.21022.08 |
| Visual C++ 2010 | 16.00.40219.01 |
| Visual C++ 2012 | 17.00.51106.1 |
| Visual C++ 2013 | 18.00.21005.1 |
| Visual C++ 2015 RTM | 19.00.23026.0 |
| Visual C++ 2015 Update 1 | 19.00.23506.0 |
| Visual C++ 2015 Update 2 | 19.00.23918.0 |
| Visual C++ 2015 Update 3 | 19.00.24215.1 |
| Visual C++ 2017 RTM | 19.10.25017.0 |
| Visual C++ 2017 versión 15.3 | 19.11.25506.0 |
| Versión 15.5 de Visual C++ 2017 | 19.12.25830.0 |
| Visual C++ 2017 versión 15.6 | 19.13.26128.0 |
| Visual C++ 2017 versión 15.7 | 19.14.26428.0 |
| Visual C++ 2017 versión 15,8 | 19.15.26726.0 |

Puede especificar solo el número principal, los números principales y secundarias o principal, secundario y números de compilación para la __/wv__ opción. El compilador informa de todas las advertencias que coinciden con las versiones que comienzan con el número especificado y suprime todas las advertencias para las versiones de mayores que el número especificado. Por ejemplo, __/Wv:17__ informa de todas las advertencias introducidas en o antes de cualquier versión de Visual Studio 2012 y suprime todas las advertencias introducidas por cualquier compilador de Visual Studio 2013 (versión 18) o posterior. Para suprimir las advertencias introducidas en Visual Studio 2015 update 2 y versiones posteriores, puede usar __/Wv:19.00.23506__. Use __/Wv:19.11__ para informar de todas las advertencias introducidas en cualquier versión de Visual Studio anteriores a Visual Studio 2017 versión 15.5, pero se suprime las advertencias introducidas en Visual Studio 2017 versión 15.5 y versiones posterior.

Las secciones siguientes enumeran las advertencias introducidas por cada versión de Visual C++ que puede suprimir con el __/wv__ opción del compilador. El __/wv__ opción no puede suprimir las advertencias que no aparecen, que son anteriores a las versiones del compilador especificadas.

## <a name="warnings-introduced-in-visual-c-2017-version-158-compiler-version-1915267260"></a>Advertencias introducidas en Visual C++ 2017 versión 15,8 (versión del compilador 19.15.26726.0)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:19.14__.

|||
|-|-|
C5046|'*función*': símbolo de que impliquen tipo con vinculación interna no definido|

## <a name="warnings-introduced-in-visual-c-2017-version-157-compiler-version-1914264280"></a>Advertencias introducidas en Visual C++ 2017 versión 15.7 (versión del compilador 19.14.26428.0)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:19.13__.

|||
|-|-|
C4642|'*problema*': no se pudo importar las restricciones del parámetro genérico '*parámetro*'
C5045|Compilador insertará la mitigación de Spectre para la carga de memoria si el modificador/qspectre especificado.

## <a name="warnings-introduced-in-visual-c-2017-version-156-compiler-version-1913261280"></a>Advertencias introducidas en Visual C++ 2017 versión 15.6 (versión del compilador 19.13.26128.0)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:19.12__.

|||
|-|-|
C5044|Un argumento de opción de línea de comandos *opción* apunta a una ruta de acceso '*ruta*' que no existe

## <a name="warnings-introduced-in-visual-c-2017-version-155-compiler-version-1912258300"></a>Advertencias introducidas en Visual C++ 2017 versión 15.5 (versión del compilador 19.12.25830.0)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:19.11__.

|||
|-|-|
C4843|'*type1*': un controlador de excepciones de referencia al tipo de matriz o función no es accesible, use '*type2*' en su lugar
C4844|"Exportar módulo *module_name*;' es ahora la sintaxis recomendada para declarar una interfaz de módulo
C5039|'*función*': puntero o referencia a una función de inicio potencialmente pasa a la función de C externa en EHc-. Si esta función produce una excepción, puede producirse un comportamiento indefinido.
C5040|especificaciones de excepción dinámicas son válidas únicamente en C ++ 14 y versiones anteriores; tratar como noexcept (false)
C5041|'*definición*': definición fuera de línea para un miembro de datos estático constexpr no es necesaria y está en desuso en C ++ 17
C5042|'*declaración*': las declaraciones de función en el ámbito de bloque no pueden ser 'inline' especificado en el estándar de C++; quite el especificador "inline"
C5043|'*especificación*': especificación de excepción no coincide con la declaración anterior

## <a name="warnings-introduced-in-visual-c-2017-version-153-compiler-version-1911255060"></a>Advertencias introducidas en Visual C++ 2017 versión 15.3 (versión del compilador 19.11.25506.0)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:19.10__.

|||
|-|-|
C4597|un comportamiento indefinido: *descripción*
C4604|'*tipo*': pasar argumentos por valor entre los límites nativo y administrado requiere un constructor de copia válido. En caso contrario, el comportamiento de tiempo de ejecución es indefinido
C4749|condicionalmente compatible: *descripción*
C4768|se omiten los atributos __declspec anteriores a la especificación de vinculación
C4834|Descartando el valor devuelto de función con el atributo "nodiscard"
C4841|extensión no estándar utilizada: *extensión*
C4842|no se garantiza el resultado de "offsetof" aplicada a un tipo mediante herencia múltiple sea consistente con las versiones del compilador
C4869|"nodiscard" solo puede aplicarse a clases, enumeraciones y funciones con el tipo de valor devuelto distinto de void
C5033|'*clase de almacenamiento*' ya no es una clase de almacenamiento compatibles
C5034|el uso de la función intrínseca '*intrínseco*' hace que la función *función* se compile como código invitado
C5035|el uso de la característica '*característica*' hace que la función *función* se compile como código invitado
C5036|conversión de puntero a la función de varargs al compilar con/Hybrid: x86arm64 '*type1*'para'*type2*'
C5037|'*función miembro*': una definición fuera de línea de un miembro de una plantilla de clase no puede tener argumentos predeterminados
C5038|miembro de datos '*member1*'se inicializará después del miembro de datos'*member2*'

## <a name="warnings-introduced-in-visual-c-2017-rtm-compiler-version-1910250170"></a>Advertencias introducidas en Visual C++ 2017 RTM (versión del compilador 19.10.25017.0)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:19.00__.

|||
|-|-|
C4468|'fallthrough': atributo debe ir seguido de una etiqueta de caso o una etiqueta predeterminada
C4698|'*característica*' es solo con fines de evaluación y está sujeta a cambios o eliminación en futuras actualizaciones.
C4839|uso no estándar de la clase*clase*' como argumento a una función variádica
C4840|uso no portable de la clase*clase*' como argumento a una función variádica

## <a name="warnings-introduced-in-visual-c-2015-update-3-compiler-version-1900242151"></a>Advertencias introducidas en Visual C++ 2015 Update 3 (versión del compilador 19.00.24215.1)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:19.00.23918__.

|||
|-|-|
C4467|uso de atributos ATL está en desuso
C4596|'*nombre*': nombre completo no válido en la declaración de miembro
C4598|' #include \< *encabezado*\>': el número de encabezado *número* en el *origen* no coincide con *origen* que posición
C4599|'*argumento*': *origen* número de argumento *número* no coincide con *origen*

## <a name="warnings-introduced-in-visual-c-2015-update-2-compiler-version-1900239180"></a>Advertencias introducidas en Visual C++ 2015 Update 2 (versión del compilador 19.00.23918.0)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:19.00.23506__.

|||
|-|-|
C4466|No se pudo realizar la elisión de montón de corrutina
C4595|'*clase*': operador no miembro new o delete funciones no pueden declararse insertadas
C4828|El archivo contiene un carácter que comienza en el desplazamiento 0 x*valor* que no es válido en el juego de caracteres de origen actual (página de códigos *número*).
C4868|compilador no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicializadores entre llaves

## <a name="warnings-introduced-in-visual-c-2015-update-1-compiler-version-1900235060"></a>Advertencias introducidas en Visual C++ 2015 Update 1 (versión del compilador 19.00.23506.0)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:19.00.23026__.

|||
|-|-|
C4426|las marcas de optimización cambiadas después de incluir el encabezado, es posible que se puede deber a #pragma optimize()
C4654|Incluir código colocado delante del encabezado precompilado de línea se omitirá. Agregue código al encabezado precompilado.
C5031|#pragma warning (POP): probable desajuste, extraer el estado de advertencia insertado en otro archivo
C5032|detectado #pragma warning (Push) con ningún Warning (POP) #pragma correspondiente

## <a name="warnings-introduced-in-visual-c-2015-rtm-compiler-version-1900230260"></a>Advertencias introducidas en Visual C++ 2015 RTM (versión del compilador 19.00.23026.0)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/wv: 18__.

|||
|-|-|
C4427|'*error*': desbordamiento de división de constantes, comportamiento no definido
C4438|'*tipo*': no se puede llamar de forma segura / await: clrcompat modo. Si '*tipo*' llama a CLR puede causar daños principal de CLR
C4455|' operador *nombre*': los identificadores de sufijo literales que no empiecen por un carácter de subrayado están reservados
C4456|declaración de '*nombre*' oculta la declaración local anterior
C4457|declaración de '*nombre*' oculta el parámetro de función
C4458|declaración de '*nombre*' oculta el miembro de clase
C4459|declaración de '*nombre*' oculta la declaración global
C4462|'*tipo*': no se puede determinar el GUID del tipo. El programa puede dar un error en tiempo de ejecución.
C4463|desbordamiento; asignar *valor* al campo de bits que solo puede contener valores de *valor* a *valor*
C4473|'*función*': no hay suficientes argumentos pasan para la cadena de formato
C4474|'*función*': pasado demasiados argumentos para la cadena de formato
C4475|'*función*': modificador de longitud '*modificador*'no puede utilizarse con el carácter de tipo'*carácter*' en el especificador de formato
C4476|'*función*': carácter de tipo desconocido '*carácter*' en el especificador de formato
C4477|'*función*': cadena de formato '*cadena*'requiere un argumento de tipo'*tipo*', pero el argumento variádico *número* tiene el tipo '*tipo*'
C4478|'*función*': no se puede combinar marcadores de posición posicionales y no posicionales en la misma cadena de formato
C4494|'*tipo*': se omite __declspec (Allocator) porque el tipo de valor devuelto de la función no es un puntero o referencia
C4495|ha utilizado una extensión '__super': reemplazar por el nombre de clase base explícito
C4496|usa una extensión no estándar 'for each': reemplazar por la instrucción ranged-for
C4497|ha utilizado una extensión 'sealed': reemplácela por 'final'
C4498|ha utilizado una extensión no estándar: '*extensión*'
C4499|'*especialización*': una especialización explícita no puede tener una clase de almacenamiento (omitida)
C4576|un tipo entre paréntesis seguido de una lista de inicializadores es una sintaxis de conversión de tipo explícita no estándar
C4577|Puede usar con ningún modo especificado; de control de excepciones 'noexcept' no se garantiza la finalización de la excepción. Especifique /EHsc
C4578|'abs': conversión de '*tipo*'para'*tipo*', posible pérdida de datos (¿pretendía llamar a '*nombre*' o a #include \<cmath >?)
C4582|'*tipo*': no se llama implícitamente constructor
C4583|'*tipo*': no se llama al destructor implícitamente
C4587|'*tipo*': cambio de comportamiento: ya no es implícitamente se llama al constructor
C4588|'*tipo*': cambio de comportamiento: ya no es implícitamente se llama al destructor
C4589|Constructor de clase abstracta*tipo*'omite el inicializador de clase base virtual'*tipo*'
C4591|límite de profundidad de llamada de 'constexpr' *número* superado (/ constexpr: Depth\<número >)
C4592|'*tipo*': símbolo dinámicamente será inicializado (limitación de implementación)
C4593|'*tipo*': límite de paso de evaluación de llamada de 'constexpr' de *valor* superado; use/constexpr: Steps\<número > para aumentar el límite
C4647|cambio de comportamiento: __is_pod (*tipo*) tiene un valor diferente en las versiones anteriores
C4648|se omite el atributo estándar 'carries_dependency'
C4649|los atributos se omiten en este contexto
C4753|No se encuentran límites para el puntero; MPX intrínseca que se ignorará
C4771|Los límites se deben crear con un puntero simple; MPX intrínseca que se ignorará
C4774|'*descripción*': se esperaba en el argumento de cadena de formato *número* no es literal de cadena
C4775|ha utilizado una extensión en la cadena de formato '*cadena*'de la función'*función*'
C4776|' %*carácter*'no se permite en la cadena de formato de la función'*función*'
C4777|'*descripción*': cadena de formato '*cadena*'requiere un argumento de tipo'*tipo*', pero el argumento variádico *número* tiene el tipo '*tipo*'
C4778|'*descripción*': sin terminar la cadena de formato '*cadena*'
C4838|conversión de '*tipo*'para'*tipo*' requiere una conversión de restricción
C5022|'*tipo*': han especificado varios constructores de movimiento
C5023|'*tipo*': varios operadores de asignación especificados
C5024|'*declaración*': mueva el constructor se definió implícitamente como eliminado
C5025|'*declaración*': mover operador de asignación se definió implícitamente como eliminado
C5026|'*tipo*': mueva el constructor se definió implícitamente como eliminado
C5027|'*tipo*': mover operador de asignación se definió implícitamente como eliminado
C5028|'*nombre*': especifica la alineación en una declaración anterior (*número*) no se especifica en la definición
C5029|extensión no estándar utilizada: los atributos de alineación en C++ se aplican a variables, los miembros de datos y solo los tipos de etiquetas
C5030|atributo '*atributo*' no se reconoce

## <a name="warnings-introduced-in-visual-c-2013-compiler-version-1800210051"></a>Advertencias introducidas en Visual C++ 2013 (versión del compilador 18.00.21005.1)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:17__.

|||
|-|-|
C4301|'*tipo*': sólo reemplazar una función virtual difiere de '*declaración*' calificador const/volatile
C4316|'*tipo*': no puede estar alineado asignado en el montón de objeto *número*
C4380|'*tipo*': un constructor predeterminado no puede estar desusado
C4388|'*token*': no coinciden signed/unsigned
C4423|'std:: bad_alloc': clase detectará ('*tipo*') en línea *número*
C4424|catch para '*tipo*'precedido por'*tipo*' en línea *número*; impredecibles comportamiento puede producir si se produce 'std:: bad_alloc'
C4425|Una anotación SAL no se puede aplicar a '...'
C4464|ruta de acceso de inclusión relativa contiene '..'
C4575|'__vectorcall' es incompatible con el ' / clr' opción: convertir a '__stdcall'
C4609|'*tipo*'se deriva de la interfaz predeterminada'*tipo*'en el tipo'*tipo*'. Use una interfaz predeterminada diferente para '*tipo*', o interrumpir la relación base/derivada.
C4754|Las reglas de conversión para las operaciones aritméticas de la comparación en *descripción*(*número*) significa que una bifurcación no se puede ejecutar. Conversión de tipos '*tipo*'para'*tipo*' (o un tipo similar de *número* bytes).
C4755|Las reglas de conversión para las operaciones aritméticas de la comparación en *descripción*(*número*) significan que una bifurcación no puede ejecutarse en una función inline. Conversión de tipos '*tipo*'para'*tipo*' (o un tipo similar de *número* bytes).
C4767|nombre de sección '*nombre*' tiene más de 8 caracteres y se truncará el vinculador
C4770|valida parcialmente enum '*nombre*' utilizar como índice
C4827|Un método 'ToString' público con 0 parámetros debe marcarse como virtual y reemplazar
C4882|pasar objetos functor con operadores de llamada no constantes a Concurrency:: parallel_for_each está en desuso
C4973|'*tipo*': marcado como en desuso
C4974|'*tipo*': marcado como en desuso
C4981|Warbird: función '*declaración*' marcada como __forceinline no está entre líneas porque contiene semántica de excepción
C4990|Warbird: *mensaje*
C4991|Warbird: función '*declaración*' marcada como __forceinline no entre líneas porque el nivel de protección de inlinee es mayor que el elemento primario
C4992|Warbird: función '*declaración*' marcada como __forceinline no entre líneas porque contiene un ensamblado alineado que no se puede proteger

## <a name="warnings-introduced-in-visual-c-2012-compiler-version-1700511061"></a>Advertencias introducidas en Visual C++ 2012 (versión del compilador 17.00.51106.1)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:16__.

|||
|-|-|
C4330|atributo '*atributo*'para la sección'*sección*' omite
C4415|duplicados __declspec (code_seg ('*nombre*'))
C4416|__declspec(code_seg(...)) contiene una cadena vacía: omite
C4417|una instancia de plantilla explícitos no code_seg: omite
C4418|__declspec(code_seg(...)) omitido en una enumeración
C4419|'*nombre*'no tiene ningún efecto cuando se aplica a la clase ref privada'*tipo*'.
C4435|'*tipo*': disposición de los objetos vd2 cambiará debido a la base virtual '*tipo*'
C4436|dynamic_cast de la base virtual '*tipo*'para'*tipo*' en el constructor o destructor podría fallar con objetos construidos parcialmente
C4437|dynamic_cast de la base virtual '*tipo*'para'*tipo*' podría producir un error en algunos contextos
C4443|se esperaba parámetro pragma fuera '0', '1' o '2'
C4446|'*tipo*': no se puede asignar el miembro '*nombre*' en este tipo, debido a un conflicto con el nombre de tipo. El método se ha cambiado a '*nombre*'
C4447|signatura 'main' encontrada sin necesidad de modelo de subprocesos. Considere usar ' int main (Platform:: Array\<Platform:: String ^ > ^ args)'.
C4448|'*tipo*' no tiene una interfaz predeterminada especificada en los metadatos. Realizar una selección: '*tipo*', que puede producir un error en tiempo de ejecución.
C4449|'*tipo*' un tipo no sellado se debe marcar como '[WebHostHidden]'
C4450|'*tipo*'se debe marcar como '[WebHostHidden]' porque deriva de'*tipo*'
C4451|'*tipo*': uso de la clase ref*tipo*' dentro de este contexto puede dar lugar a la serialización no válido del objeto en todos los contextos
C4452|'*tipo*': no puede ser un tipo público en el ámbito global. Debe estar en un espacio de nombres es un elemento secundario del nombre del archivo de salida .winmd.
C4453|'*tipo*': un tipo '[WebHostHidden]' no debe usarse en la superficie publicada de un tipo público que no sea '[WebHostHidden]'
C4454|'*tipo*' está sobrecargado por algo más que el número de parámetros de entrada sin necesidad de especificado [DefaultOverload]. Seleccionar '*declaración*' como sobrecarga predeterminada
C4471|'*nombre*': una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente (se presupone int)
C4472|'*nombre*' es una enumeración nativa: agregue un especificador de acceso (privado/público) para declarar una enumeración administrada o WinRT
C4492|'*tipo*': coincide con el método de clase ref de base '*tipo*', pero no está marcado como 'override'
C4493|Expresión DELETE no tiene ningún efecto porque el destructor de '*tipo*' no tiene accesibilidad 'public'
C4585|'*tipo*': clase no sellada A WinRT 'public ref class' debe estar sellado o derivar de una existente
C4586|'*tipo*': no se puede declarar un tipo público en un espacio de nombres de nivel superior llamado 'Windows'
C4695|#pragma execution_character_set: '*argumento*' no es un argumento admitido: se admite actualmente solo "UTF-8"
C4703|variable de puntero local potencialmente no inicializada '*nombre*' utiliza
C4728|/ Opción Yl-omitida porque se requiere la referencia PCH
C4745|acceso volátil de '*nombre*' no se puede respetar debido a su tamaño
C4746|acceso volátil de '*nombre*' está sujeta a /volatile:\<iso\|ms >; considere el uso de funciones intrínsecas __iso_volatile_load/store
C4872|división de punto flotante por cero detectado al compilar el gráfico de llamadas para Concurrency:: parallel_for_each en: '*descripción*'
C4880|realiza la conversión de '*tipo*'para'*tipo*': desechar la declaración de un puntero o referencia puede provocar un comportamiento indefinido en una función de la restricción de amp
C4881|el constructor o destructor no se invocará para la variable tile_static '*tipo*'
C4966|'*descripción*' tiene una anotación __code_seg con nombre de segmento no admitido; anotación omitida
C4988|'*tipo*': variable declarada fuera del ámbito de clase o función
C4989|'*descripción*': tipo tiene definiciones en conflicto.

## <a name="warnings-introduced-in-visual-c-2010-compiler-version-16004021901"></a>Advertencias introducidas en Visual C++ 2010 (versión del compilador 16.00.40219.01)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:15__.

|||
|-|-|
C4352|'*nombre*': función intrínseca ya definida
C4573|el uso de '*tipo*' requiere que el compilador capture 'this' pero no permitir que el modo de captura predeterminado actual
C4574|'*nombre*'se define como ' 0': ¿pretendía usar ' #if *nombre*'?
C4689|'*carácter*': carácter no admitido en #pragma detect_mismatch; #pragma omitidas
C4751|marca /arch AVX no es aplicable a Intel (r) extensiones SIMD de Streaming que están en ASM inline
C4752|encontrar extensiones de Vector avanzadas de Intel (r); Considere el uso de la marca /arch AVX adecuada
C4837|se detectó un trígrafo: '?? *carácter*'reemplazado por'*carácter*'
C4986|'*declaración*': especificación de excepción no coincide con la declaración anterior
C4987|se usó una extensión no estándar: 'throw (...)'

## <a name="warnings-introduced-in-visual-c-2008-compiler-version-15002102208"></a>Advertencias introducidas en Visual C++ 2008 (versión del compilador 15.00.21022.08)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:14__.

|||
|-|-|
C4396|'*tipo*': el especificador inline no se puede usar cuando una declaración friend hace referencia a una especialización de una plantilla de función
C4413|'*declaración*': miembro de referencia se inicializa en un archivo temporal que no se conserva cuando termina el constructor
C4491|'*descripción*': tiene un formato de versión IDL no válido
C4603|'*nombre*': no está definida la macro o definición es diferente después del uso del encabezado precompilado
C4627|'*descripción*': omite al buscar el precompilado uso del encabezado
C4750|'*descripción*': función con _alloca () insertada en un bucle
C4910|'*tipo*': '__declspec (dllexport)' y 'extern' son incompatibles en una instancia explícita
C4985|'*declaración*': atributos no presentes en la declaración anterior.

## <a name="warnings-introduced-in-visual-c-2005-compiler-version-140050727762"></a>Advertencias introducidas en Visual C++ 2005 (versión del compilador 14.00.50727.762)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:13__.

|||
|-|-|
C4000|Advertencia desconocida elija el comando soporte técnico en el menú Ayuda de Visual C++, o abra el archivo de Ayuda de soporte técnico para obtener más información
C4272|'*tipo*': está marcado como __declspec (dllimport); debe especificar la convención de llamadas nativa al importar una función.
C4333|'*expresión*': desplazamiento a la derecha por cantidad demasiado grande, la pérdida de datos
C4334|'*expresión*': el resultado del desplazamiento de 32 bits se convierte implícitamente en 64 bits (era quería un desplazamiento de 64 bits?)
C4335|Formato de archivo Mac detectado: convierta el archivo de origen en formato DOS o UNIX
C4342|cambio de comportamiento: '*tipo*' llama a, pero se llamó a un operador de miembro en las versiones anteriores
C4350|cambio de comportamiento: '*declaración*'llama a en lugar de'*declaración*'
C4357|argumento de matriz de parámetro se encuentra en la lista de argumentos formal para el delegado '*declaración*'se omite cuando se genera'*tipo*'
C4358|'*expresión*': tipo de valor devuelto de los delegados combinados no es 'void'; el valor devuelto es indefinido
C4359|'*tipo*': especificador de alineación es menor que la alineación real (*número*) y se omitirá.
C4362|'*tipo*': CLR no admite alineaciones mayores de 8 bytes
C4364|#using para el ensamblado '*nombre*' ya aparecía previamente en *descripción*(*número*) sin el atributo as_friend; as_friend no aplicado
C4365|'*expresión*': conversión de '*tipo*'para'*tipo*', no coinciden signed/unsigned
C4366|El resultado de que el operador unario '*operador*' operador se puede desalinear
C4367|Conversión de '*tipo*'para'*tipo*' puede provocar la excepción de desalineación de tipo de datos
C4368|no se puede definir '*nombre*'como administrado de un miembro de'*tipo*': no se admiten tipos mixtos
C4369|'*tipo*': valor de enumerador '*número*'no se puede representar como'*tipo*', valor es'*número*'
C4374|'*declaración*': no se implementará el método de interfaz mediante el método no virtual '*declaración*'
C4375|el método no público '*declaración*'no invalida'*declaración*'
C4376|especificador de acceso '*especificador*:' ya no se admite: utilice '*especificador*:' en su lugar
C4377|tipos nativos son privados de forma predeterminada; -d1PrivateNativeTypes está en desuso
C4378|Debe obtener punteros a función para ejecutar a los inicializadores; ModuleHandle:: ResolveMethodHandle
C4379|Versión *versión* de common language runtime no es compatible con este compilador. Con esta versión puede provocar resultados inesperados
C4381|'*declaración*': no se implementará el método de interfaz mediante el método no público '*declaración*'
C4382|Iniciando '*tipo*': solamente se puede detectar un tipo con el destructor __clrcall o el constructor de copias en/CLR: pure módulo
C4383|'*tipo*': el significado de desreferenciar un identificador puede cambiar cuando definido por el usuario '*operador*' operador existe; escriba el operador como función estática para que sea explícito sobre el operando
C4384|#pragma '*directiva*' solo debe usarse en el ámbito global
C4393|'*tipo*': const no tiene ningún efecto *descripción* miembro de datos; omite
C4394|'*tipo*': símbolo por appdomain no se debe marcar con __declspec (*valor*)
C4395|'*tipo*': función miembro se invocará en una copia del miembro de datos initonly '*tipo*'
C4397|DefaultCharSetAttribute se pasa por alto
C4398|'*tipo*': objeto global por proceso no funcionen correctamente con varios dominios de aplicación; utilice __declspec (AppDomain)
C4399|'*tipo*': símbolo por proceso no se debe marcar con __declspec (*valor*) cuando se compila con/CLR: pure
C4400|'*tipo*': no se admiten los calificadores const/volatile en este tipo
C4412|'*declaración*': función firma contiene el tipo '*tipo*'; Los objetos de C++ son no es seguro pasar entre código puro y mixto o nativo.
C4429|posible incompleto o incorrectamente formado universal: nombre de carácter
C4430|falta el especificador de tipo; se presupone int. Nota: C++ no admite default-int
C4431|falta el especificador de tipo; se presupone int. Nota: C no admite default-int
C4434|un constructor estático debe tener accesibilidad privada; cambiará a acceso privado
C4439|'*tipo*': definición de función con un tipo administrado en la firma debe tener una convención de llamada __clrcall
C4441|convención de llamada de '*convención*' omitida; '*convención*' utilizado en su lugar
C4445|'*declaración*': un método virtual no puede ser privado en un tipo administrado o WinRT
C4460|Operador CLR o WinRT '*tipo*', tiene un parámetro pasado por referencia. Operador CLR o WinRT '*operador*'tiene una semántica diferente del operador de C++'*operador*', ¿deseaba pasar por valor?
C4461|'*tipo*': esta clase tiene un finalizador '! *tipo*' pero no un destructor ' ~*tipo*'
C4470|pragmas de control de punto flotante omitidas en /clr
C4480|extensión no estándar utilizada: especifica el tipo subyacente de enum '*tipo*'
C4481|ha utilizado una extensión no estándar: especificador de invalidación '*especificador*'
C4482|ha utilizado una extensión no estándar: enumeración '*tipo*' utilizado en el nombre completo
C4483|error de sintaxis: se esperaba la palabra clave de C++
C4484|'*tipo*': coincide con el método de clase ref de base '*tipo*', pero no está marcado como 'virtual', 'new' u 'override'; se supone 'new' (y no 'virtual')
C4485|'*tipo*': coincide con el método de clase ref de base '*tipo*', pero no está marcada 'new' u 'override'; se supone 'new' (y 'virtual')
C4486|'*tipo*': un método virtual privado de una clase ref o clase value debe marcarse como 'sealed'
C4487|'*tipo*': coincide con hereda el método no virtual '*tipo*' pero no está explícitamente marcado como 'new'
C4488|'*tipo*': requiere '*palabra clave*'palabra clave para implementar el método de interfaz'*tipo*'
C4489|'*palabra clave*': no se permite en el método de interfaz '*nombre*'; solo se permiten especificadores en métodos de clase de valor y de clase ref de invalidación
C4490|'*palabra clave*': uso incorrecto del especificador de invalidación; '*tipo*' no coincide con un método de clase ref base
C4538|'*tipo*': no se admiten los calificadores const/volatile en este tipo
C4559|'*tipo*': redefinición; el __declspec ganancias de función (*valor*)
C4565|'*tipo*': redefinición; el símbolo se declaró previamente con __declspec (*valor*)
C4566|carácter representado por el nombre de carácter universal '*carácter*' no se puede representar en la página de códigos actual (*número*)
C4568|'*tipo*': ningún miembro coincide con la firma de la invalidación explícita
C4569|'*tipo*': ningún miembro coincide con la firma de la invalidación explícita
C4570|'*tipo*': no se declara explícitamente como abstracto pero tiene funciones abstractas
C4571|Informativo: semántica de catch (...) cambiada desde Visual C++ 7.1; ya no se detectan excepciones estructuradas (SEH)
C4572|El atributo [ParamArray] está desusado en /clr; use '...' en su lugar
C4580|[atributo] está desusado; en su lugar, especifique *especificado*atributo como una clase base
C4581|comportamiento desusado: ' "*nombre*"' reemplazado por '*nombre*' para procesar el atributo
C4606|Advertencia de #pragma: '*número*' omitida; Advertencias de análisis de código no están asociadas con niveles de advertencia
C4631|MSXML o XPath no disponible; no se procesarán los comentarios del documento XML. *description*
C4632|Comentario del documento XML: *descripción* -acceso denegado: *descripción*
C4633|Comentario del documento XML*descripción*: error: *descripción*
C4634|Comentario del documento XML*descripción*: no se puede aplicar: *descripción*
C4635|Comentario del documento XML*descripción*: XML incorrectamente formado: *descripción*
C4636|Comentario del documento XML*descripción*: la etiqueta requiere vacío '*descripción*' atributos.
C4637|Comentario del documento XML*descripción*: \<incluyen > etiqueta descartado. *description*
C4638|Comentario del documento XML*descripción*: referencia a símbolo desconocido '*descripción*'.
C4639|Error MSXML, documento XML no se procesarán los comentarios. *description*
C4641|Comentario del documento XML tiene una referencia cruzada ambigua:
C4678|clase base*declaración*'es menos accesible que'*nombre*'
C4679|'*descripción*': no se pudo importar el miembro
C4687|'*tipo*': una clase abstracta sellada no puede implementar una interfaz '*tipo*'
C4688|'*nombre*': lista de restricciones contiene un tipo privado de ensamblado '*declaración*'
C4690|\[ emitidl (pop)]: más elementos POP que Push
C4691|'*tipo*': se esperaba el tipo al que hace referencia en sin referencia *módulo* '*descripción*', tipo definido en la unidad de traducción actual utilizado en su lugar
C4692|'*nombre*': firma de un miembro no privado contiene el tipo nativo privado de ensamblado '*declaración*'
C4693|'*tipo*': una clase abstracta sellada no puede tener los miembros de cualquier instancia*nombre*'
C4694|'*tipo*': una clase abstracta sellada no puede tener una clase base*tipo*'
C4720|informes de ensamblado en línea: '*descripción*'
C4721|'*descripción*': no está disponible como intrínseco
C4722|'*descripción*': destructor nunca devuelve un valor, posible pérdida de memoria
C4726|ARM arch4/4T solamente admite '\<cpsr_f > o \<spsr_f >' con un valor inmediato
C4727|PCH denominado *nombre* con la misma marca de tiempo en *nombre* y *nombre*.  Usar el primer PCH.
C4729|función demasiado grande para advertencias basadas en gráficos de flujos
C4730|'*descripción*': mezcla de _m64 y expresiones pueden ocasionar código incorrecto de punto flotante
C4731|'*descripción*': registro de puntero de marco '*registrar*' modificado por código de ensamblado alineado
C4732|intrínseco '*intrínseco*' no se admite en esta arquitectura
C4733|Inline asm que asigna a 'FS: 0': controlador no está registrado como controlador seguro
C4734|Más de 64k; sección de información de depuración de números de línea en un formato COFF Detenga la emisión de números de línea de depuración COFF para el módulo '*módulo*'
C4738|almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento
C4739|referencia a la variable '*variable*' supera su espacio de almacenamiento
C4740|flujo dentro o fuera del código inline asm suprime la optimización global
C4742|'*variable*'tiene una alineación diferente '*ubicación*'y'*ubicación*': *número* y *número*
C4743|'*nombre*'tiene un tamaño diferente '*ubicación*'y'*ubicación*': *número* y *número* bytes
C4744|'*nombre*'tiene un tipo diferente '*ubicación*'y'*ubicación*': '*tipo*'y'*tipo*'
C4747|Una llamada a administrado '*tipo*': no se puede ejecutar código administrado en un bloqueo del cargador, incluido el DLL entrypoint y las llamadas alcanzadas desde el punto
C4761|tamaño integral no coincide en el argumento; conversión proporcionada
C4764|No se pueden alinear objetos detectados con elementos mayores de 16 bytes
C4788|'*identificador*': identificador se ha truncado a '*número*' caracteres
C4789|búfer '*nombre*' del tamaño *número* bytes producirá una saturación del; *número* se escribirán bytes empezando en el desplazamiento *número*
C4801|Si la devolución por referencia no es comprobable: *descripción*
C4819|El archivo contiene un carácter que no se puede representar en la página de códigos actual (*número*). Guarde el archivo en formato Unicode para evitar la pérdida de datos
C4826|Conversión de '*tipo*'para'*tipo*' extensión de signo. Esto puede provocar un comportamiento inesperado en tiempo de ejecución.
C4829|Parámetros posiblemente incorrectos para la función main. Considere ' int main (Platform:: Array\<Platform:: String ^ > ^ argv)'
C4835|'*tipo*': el inicializador para los datos exportados no se ejecutará hasta que el código administrado se ejecuta en primer lugar en el ensamblado de host
C4867|'*tipo*': sintaxis no estándar; utilice '&' para crear un puntero a miembro
C4936|__declspec se admite solamente cuando se compila con /clr o /clr:pure
C4937|'*nombre*'y'*nombre*'son pueden distinguir como argumentos a'*opción*'
C4938|'*tipo*': variable de reducción de punto flotante puede causar resultados incoherentes bajo/fp: strict o #pragma fenv_access
C4939|#pragma vtordisp está en desuso y se quitará en una próxima versión de Visual C++
C4947|'*tipo*': marcado como obsoleto
C4949|pragmas 'managed' y 'unmanaged' solamente son significativas cuando se compilan con ' / clr [: opción]'
C4950|'*tipo*': marcado como obsoleto
C4955|'*descripción*': importación omitida; ya se importó desde '*origen*'
C4956|'*tipo*': este tipo no es comprobable
C4957|'*expresión*': conversión explícita de '*tipo*'para'*tipo*' no es comprobable
C4958|'*expresión*': la aritmética con punteros no es comprobable
C4959|no se puede definir no administrado *clase* '*tipo*' en/CLR: safe porque el acceso a sus miembros proporciona código no comprobable
C4960|'*descripción*' es demasiado grande para generar un perfil
C4961|No se combinó ningún perfil de datos '*ubicación*', deshabilitado las optimizaciones guiadas por perfil
C4962|'*descripción*': las optimizaciones guiadas por perfil deshabilitadas porque generaban datos de perfil incoherentes
C4963|'*descripción*': se encontró ningún perfil de datos; se utilizaron opciones de compilador diferentes en la compilación instrumentada
C4964|Se especificó ninguna opción de optimización; no se recopilará la información de perfil
C4965|conversión boxing implícita de entero 0; Utilice nullptr o conversión explícita
C4970|constructor delegado: objeto de destino se omite desde '*declaración*' es estático
C4971|Orden de argumentos: \<objeto de destino >, \<función de destino > para el constructor delegado está en desuso, utilice \<función de destino >, \<objeto de destino >
C4972|No se puede comprobar la modificación o el tratamiento directo del resultado de una operación de conversión unbox como valor L

## <a name="warnings-introduced-in-visual-c-2003-compiler-version-13103077"></a>Advertencias introducidas en Visual C++ 2003 (versión del compilador 13.10.3077)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:13.00.9466__.

|||
|-|-|
C4343|#pragma optimize (*descripción*, off) invalida la opción /Og
C4344|cambio de comportamiento: uso de los resultados de argumentos de plantilla explícitos en la llamada a '*declaración*'
C4346|'*tipo*': nombre dependiente no es un tipo
C4348|'*declaración*': nueva definición de parámetro predeterminado: parámetro *número*
C4356|'*tipo*': no se puede inicializar el miembro de datos estático mediante una clase derivada
C4408|anónimo *struct* no se ha declarado ningún miembro de datos
C4544|'*declaración*': argumento de plantilla que se omite en esta declaración de plantilla predeterminado
C4545|la expresión antes de la coma se evalúa como una función a la que le falta una lista de argumentos
C4546|falta la lista de argumentos de la llamada de función antes de la coma
C4547|'*expresión*': operador antes de una coma no tiene ningún efecto; se esperaba un operador con efectos secundarios
C4548|la expresión antes de la coma no tiene ningún efecto; se esperaba una expresión con efectos secundarios
C4549|'*expresión*': operador antes de la coma no tiene ningún efecto; ¿realmente pensaba en '*expresión*'?
C4628|los digramas no son compatibles con -Ze. Secuencia de caracteres '*secuencia*'no interpretado como token alternativo de'*token*'
C4629|digrama utilizado, secuencia de caracteres '*secuencia*'interpretado como símbolo (token)'*token*' (Inserte un espacio entre los dos caracteres si esto no es lo intentaba)
C4671|'*descripción*': el constructor de copia es inaccesible
C4676|'*descripción*': el destructor no es accesible
C4677|'*nombre*': signatura de miembro no privado contiene un tipo privado de ensamblado '*declaración*'
C4686|'*tipo*': posible cambio de comportamiento, cambio en el UDT devolver la convención de llamada
C4812|estilo de declaración obsoleto: utilice '*tipo*::*nombre*' en su lugar
C4813|'*tipo*': debe haber declarado anteriormente una función friend de una clase local
C4821|No se puede determinar el tipo de codificación Unicode guarde el archivo con signatura (BOM)
C4822|'*tipo*': función miembro de clase local no tiene un cuerpo
C4823|'*tipo*': utiliza punteros anclados pero desenredo semántica no está habilitada. Considere el uso de /EHa
C4913|el operador binario ',' definido por el usuario existe pero ninguna sobrecarga puede convertir todos los operandos; en su lugar, se utilizará el operador binario ',' incorporado
C4948|tipo de valor devuelto '*declaración*' no coincide con el tipo último parámetro de un establecedor correspondiente
C4951|'*descripción*' se ha editado desde que se recopilaron los datos, los datos de perfil de función no usa de perfil
C4952|'*descripción*': se encontró ningún perfil de datos en la base de datos de programa '*descripción*'
C4953|Inlinee '*descripción*' se ha editado desde que se recopilaron los datos, datos de perfil no utilizados de perfil
C4954|'*descripción*': no perfilado (contiene la expresión switch __int64)

## <a name="warnings-introduced-in-visual-c-2002-compiler-version-13009466"></a>Advertencias introducidas en Visual C++ 2002 (versión del compilador 13.00.9466)

Estas advertencias y todas las advertencias en versiones posteriores se suprimen con la opción del compilador __/Wv:12__.

|||
|-|-|
C4096|'*tipo*': no es una interfaz COM de interfaz; no se emitirá para IDL
C4097|se esperaba que el parámetro de tipo pragma fuera 'restore' u 'off'
C4165|'HRESULT' se está convirtiendo en 'bool'; ¿está seguro de que desea realizar esta operación?
C4183|'*nombre*': falta el tipo de valor devuelto; se supone que una función miembro devuelve 'int'
C4199|*description*
C4255|'*nombre*': no se ha proporcionado un prototipo de función: convirtiendo '()' a '(void)'
C4256|'*declaración*': constructor de clase con bases virtuales tiene '...'; las llamadas pueden no ser compatibles con versiones anteriores de Visual C++
C4258|'*nombre*': definición de la de bucle se omite; se utiliza la definición del ámbito envolvente
C4263|'*declaración*': función miembro no invalida ninguna función miembro virtual de clase base
C4264|'*declaración*': no hay un reemplazo disponible para la función miembro virtual desde la base '*clase*'; la función está oculta
C4265|'*tipo*': clase tiene funciones virtuales, pero el destructor no es virtual instancias de esta clase no se destruyan correctamente
C4266|'*declaración*': no hay un reemplazo disponible para la función miembro virtual desde la base '*clase*'; la función está oculta
C4267|'*expresión*': conversión de 'size_t' a '*tipo*', posible pérdida de datos
C4274|#ident omitido; Consulte la documentación de #pragma comment (exestr, 'string')
C4277|elemento importado '*tipo*::*nombre*' existe como miembro de datos y miembro de función; ha omitido el miembro de datos
C4278|'*nombre*': identificador de la biblioteca de tipos '*descripción*' ya es una macro; utilice el calificador 'rename'
C4279|'*nombre*': identificador de la biblioteca de tipos '*descripción*' es una palabra clave; utilice el calificador 'rename'
C4287|'*expresión*': no coinciden las constantes sin signo o negativas
C4288|ha utilizado una extensión no estándar: '*nombre*': variable de control de bucles declarada en el bucle for se utiliza fuera del ámbito del bucle for; origina conflictos con la declaración en el ámbito externo
C4289|ha utilizado una extensión no estándar: '*nombre*': variable de control de bucles declarada en el bucle for se utiliza fuera del ámbito del bucle for
C4293|'*expresión*': desplazar un recuento negativo o demasiado grande; comportamiento impredecible
C4295|'*tipo*': matriz es demasiado pequeña para incluir un carácter nulo de terminación
C4296|'*expresión*': la expresión es siempre *valor*
C4297|'*tipo*': función supone que no se inicia una excepción, pero lo hace
C4298|'*nombre*': identificador de la biblioteca de tipos '*descripción*' ya es una macro; cambiar el nombre a ' __*nombre*'
C4299|'*nombre*': identificador de la biblioteca de tipos '*descripción*' es una palabra clave; cambiar el nombre a ' __*nombre*'
C4302|'*expresión*': truncamiento de '*tipo*'para'*tipo*'
C4303|*conversión* desde '*tipo*'para'*tipo*' está en desuso, utilice static_cast, __try_cast o dynamic_cast
C4314|se esperaba parámetro pragma fuera '32' o '64'
C4315|'*tipo*': puntero 'this' para el miembro '*tipo*' no puede estar alineado *número* según lo previsto por el constructor
C4318|transmisión de constante cero como la longitud para memset
C4319|'*expresión*': extensión de cero '*tipo*'para'*tipo*' de mayor tamaño
C4321|genera de forma automática un IID para la interfaz '*tipo*'
C4322|generar automáticamente un CLSID para la clase*tipo*'
C4323|reutilizando CLSID registrado para la clase*tipo*'
C4324|'*tipo*': se rellenó la estructura debido al especificador de alineación
C4325|los atributos de sección estándar '*descripción*' omite
C4326|tipo de valor devuelto '*nombre*'debe ser'*tipo*'en lugar de'*tipo*'
C4327|'*expresión*': alineación del direccionamiento indirecto de LHS (*número*) es mayor que la de RHS (*número*)
C4328|'*descripción*': alineación del direccionamiento indirecto del parámetro formal *número* (*número*) es mayor que la alineación del argumento real (*número*)
C4329|se omite el especificador de alineación en la enumeración
C4336|importar la biblioteca de tipos '*biblioteca*'antes de importar'*descripción*'
C4337|la biblioteca de tipos '*biblioteca*'in'*descripción*' se importa automáticamente
C4338|#pragma *descripción*: sección estándar '*sección*' se usa
C4339|'*tipo*': detectó el uso de un tipo no definido en los metadatos CLR o WinRT - uso de este tipo puede provocar una excepción en tiempo de ejecución
C4353|ha utilizado una extensión no estándar: constante 0 como expresión de función.  Utilice en su lugar '__noop' función intrínseca
C4370|'*declaración*': diseño de clase cambió desde una versión anterior del compilador debido a una mejora del empaquetado
C4371|'*declaración*': el diseño de clase puede haber cambiado desde una versión anterior del compilador debido a una mejora del empaquetado del miembro '*miembro*'
C4373|'*tipo*': la invalidación de funciones virtuales*declaración*', las versiones anteriores del compilador no se reemplazaron cuando los parámetros solo se diferenciaban en los calificadores const y volatile
C4387|'*descripción*': se consideraba
C4389|'*expresión*': no coinciden signed/unsigned
C4391|'*declaración*': tipo de valor devuelto incorrecto para la función intrínseca, se esperaba '*tipo*'
C4392|'*declaración*': número incorrecto de argumentos para la función intrínseca, se esperaba '*número*' argumentos
C4407|conversión entre diferentes representaciones de puntero a miembro, el compilador puede generar código incorrecto
C4420|'*nombre*': operador no está disponible, utilizando '*nombre*' en su lugar; comprobación de tiempo de ejecución puede suponer un riesgo
C4440|nueva definición de convención de llamada '*descripción*'para'*descripción*' omite
C4442|terminador nulo incrustado en el argumento __annotation.  Valor se truncará.
C4444|'*nombre*': el nivel superior '__unaligned' no está implementado en este contexto
C4526|'*tipo*': función miembro estática no puede invalidar la función virtual '*declaración*' se omite, el reemplazo se ocultará la función virtual
C4531|Control de excepciones de C++ no está disponible en Windows CE. Utilice el control de excepciones estructurado
C4532|'*descripción*': saltar fuera de *finalmente* bloque tiene un comportamiento indefinido durante el control de finalización
C4533|inicialización de '*declaración*' se omite en ' goto *declaración*'
C4534|'*declaración*' no será un constructor predeterminado para *clase* '*tipo*' debido al argumento predeterminado
C4535|llamar a _set_se_translator () requiere /EHa
C4536|'*descripción*': nombre de tipo supera el límite de metadatos de '*número*' caracteres
C4537|'*declaración*': '.' aplicado al tipo no definido por el usuario
C4542|Omitiendo la generación del archivo de texto insertado combinado, no se puede escribir *tipo* archivo: '*filename*': *error*
C4543|Inserta texto suprimido por el atributo ' ningún\_injected_text'
C4555|la expresión no tiene efecto; se esperaba una expresión con efecto secundario
C4557|'__assume' contiene el efecto '*efecto*'
C4558|valor del operando '*número*'está fuera del intervalo'*número* - *número*'
C4561|'__fastcall' es incompatible con el ' / clr' opción: convertir a '__stdcall'
C4562|se requieren funciones prototipos totalmente con el ' / clr' opción: convirtiendo '()' a '(void)'
C4564|método '*nombre*' de *clase* '*tipo*'define un parámetro predeterminado no admitido'*parámetro*'
C4584|'*tipo*': clase base*declaración*'ya es una clase base de'*declaración*'
C4608|Inicializando varios miembros de unión: '*tipo*'y'*tipo*'
C4619|#pragma warning: no hay ningún número de advertencia '*número*'
C4623|'*tipo*': constructor predeterminado se definió implícitamente como eliminado
C4624|'*tipo*': destructor se definió implícitamente como eliminado
C4625|'*tipo*': constructor de copias se definió implícitamente como eliminado
C4626|'*tipo*': operador de asignación se definió implícitamente como eliminado
C4645|función declarada con 'noreturn' tiene una instrucción return
C4646|función declarada con 'noreturn' tiene el tipo de valor devuelto distinto de void
C4659|#pragma '*descripción*': uso del segmento reservado '*nombre*' con un comportamiento indefinido, utilice #pragma comment (linker,...)
C4667|'*declaración*': ninguna plantilla de función definida que coincida con creación de instancias forzada
C4668|'*nombre*'no está definido como macro de preprocesador y se reemplaza por '0' para'*valor*'
C4669|'*expresión*': conversión no segura: '*tipo*' es un objeto de tipo administrado o WinRT
C4674|'*nombre*' se debe declarar como 'static' y tener exactamente un parámetro
C4680|'*tipo*': coclase no especifica una interfaz predeterminada
C4681|'*tipo*': coclase no especifica una interfaz predeterminada que sea un origen de eventos
C4682|'*tipo*': ningún parámetro direccional especificado, un atributo [in]
C4683|'*declaración*': origen de eventos tiene un 'out'-parámetro; tenga cuidado al enlazar varios controladores de eventos
C4684|'*descripción*': advertencia!! atributo puede causar una generación de código no válido: usar con precaución
C4685|se esperaba '> >' pero se encontró '>>' al analizar los parámetros de plantilla
C4700|variable local sin inicializar '*nombre*' utiliza
C4701|variable local potencialmente no inicializada '*nombre*' utiliza
C4702|código inaccesible
C4711|función '*nombre*' seleccionada para expansión automática alineada
C4714|función '*declaración*' marcada como __forceinline no está entre líneas
C4715|'*función*': no todas las rutas de acceso de control devuelven un valor
C4716|'*función*': debe devolver un valor
C4717|'*función*': recursiva en todas las rutas de control, función provocará el desbordamiento de pila en tiempo de ejecución
C4718|'*función*': llamada recursiva no tiene efectos secundarios, eliminar
C4719|Al especificar Qfast - utilice 'f' como sufijo para indicar precisión sencilla se encontró una constante doble
C4723|posible división por 0
C4724|posible división (módulo) por 0
C4725|puede que la instrucción máquina sea incorrecta en algunos equipos Pentium
C4757|el subíndice es un valor grande sin signo, ¿realmente pensaba en una constante negativa?
C4772|#import hace referencia a un tipo de una biblioteca de tipos que faltan; '*descripción*' utilizado como marcador de posición
C4792|función '*función*' declarada usando sysimport y que se hace referencia desde código nativo; biblioteca de importación requerida para vincular
C4794|segmento de variable de almacenamiento local de subproceso '*nombre*'cambió de'*segmento*'para'*segmento*'
C4798|código nativo generado para la función de código empaquetado '*nombre*' con el controlador de excepciones o semántica de desenredo
C4799|función '*nombre*' tiene una instrucción máquina EMMS
C4803|'*declaración*': el método raise tiene una clase de almacenamiento distinta de la del evento, '*declaración*'
C4810|valor de pragma Pack (Show) == *número*
C4811|valor de pragma conform (forScope, show) == *valor*
C4820|'*tipo*': '*número*' bytes de relleno agregados después *tipo* '*tipo*'
C4905|literal de cadena ancho puede convertir a '*tipo*'
C4906|convertir en literal de cadena '*tipo*'
C4912|'*atributo*': atributo de comportamiento no definido en un UDT anidado
C4916|para tener un dispid, '*tipo*': debe ser producido por una interfaz
C4917|'*tipo*': un GUID solo puede asociarse con una clase, interfaz o espacio de nombres
C4918|'*carácter*': carácter no válido en la lista de optimizaciones de pragma
C4920:|enumeración *nombre* miembro *nombre*=*número* ya se ha visto en la enumeración *nombre* como *nombre* = *número*
C4921|'*nombre*': valor del atributo '*valor*' no se debe especificar varias veces
C4925|'*declaración*': no se puede llamar al método dispinterface desde el script
C4926|'*declaración*': ya se ha definido el símbolo: omitido los atributos
C4927|conversión no válida; se aplicó implícitamente más de una conversión definida por el usuario
C4928|inicialización de copia no válida; se aplicó implícitamente más de una conversión definida por el usuario
C4929|'*descripción*': biblioteca de tipos contiene una unión; se omitirá el calificador 'embedded_idl'
C4930|'*declaración*': no se llama a la función prototipo (era pensada una definición de variable?)
C4931|se supone que se creó la biblioteca de tipos para *número*-bit punteros
C4932|__identifier (*descripción*) e __identifier (*descripción*) son indistinguibles
C4934|'__delegate (Multicast)' está en desuso; utilice '__delegate' en su lugar
C4935|especificador de acceso de ensamblado modificado de '*descripción*'
C4944|'*nombre*': no se puede importar un símbolo desde '*origen*': como*declaración*' ya existe en el ámbito actual
C4945|'*nombre*': no se puede importar un símbolo desde '*origen*': como*declaración*'ya se importó desde otro ensamblado'*origen*'
C4946|se utilizó reinterpret_cast entre clases relacionadas: '*declaración*'y'*declaración*'
C4995|'*nombre*': se marcó el nombre como #pragma deprecated
C4996|'*problema*': *descripción*
C4997|'*tipo*': coclase no implementa una pseudointerfaz o interfaz COM
C4998|Error de EXPECTATIVA: *descripción*(*número*)

## <a name="see-also"></a>Vea también

- [Opción del compilador/wv](../../build/reference/compiler-option-warning-level.md)
- [Advertencias del compilador que están desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md)
- [warning](../../preprocessor/warning.md)
