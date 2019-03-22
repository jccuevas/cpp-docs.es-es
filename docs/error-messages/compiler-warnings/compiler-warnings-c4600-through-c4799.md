---
title: Compilador advertencias C4600 a C4799
ms.date: 07/03/2018
f1_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
helpviewer_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: d1b1e06d3a2be71d6386554c704c547c6f2a4672
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328379"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>Compilador advertencias C4600 a C4799

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de advertencia generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Mensajes de advertencia

|Advertencia|Mensaje|
|-------------|-------------|
|[Advertencia del compilador (nivel 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma 'macro name': se esperaba una cadena vacía no válida|
|[Advertencia del compilador (nivel 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: 'macro name' ninguna #pragma push_macro anterior para este identificador|
|[Advertencia del compilador (nivel 1) C4603](compiler-warning-level-1-c4603.md)|'*identificador*': no está definida la macro o definición es diferente después del uso del encabezado precompilado|
|Advertencia del compilador (nivel 1) C4604|'*tipo*': pasar argumentos por valor entre los límites nativo y administrado requiere un constructor de copia válido. En caso contrario, el comportamiento de tiempo de ejecución es indefinido|
|Advertencia del compilador (nivel 1) C4605|' /D*macro*' especificado en la línea de comandos actual, pero no se especificó cuando se creó el encabezado precompilado|
|[Advertencia del compilador (nivel 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|Advertencia de #pragma: 'número de advertencia' omitida; Advertencias de análisis de código no están asociadas con niveles de advertencia|
|[Advertencia del compilador (nivel 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|“union_member” ya ha sido inicializado por otro miembro union en la lista de inicializadores, “union_member”|
|Advertencia del compilador (nivel 3, Error) C4609|'*type1*'se deriva de la interfaz predeterminada'*interfaz*'en el tipo'*type2*'. Use una interfaz predeterminada diferente para '*type1*', o interrumpir la relación base/derivada.|
|[Advertencia del compilador (nivel 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|nunca se puede crear instancias de objeto 'class': requerido un constructor definido por el usuario|
|[Advertencia del compilador (nivel 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|interacción entre 'función' y la destrucción de objetos de C++ no es transportable|
|[Advertencia del compilador (nivel 1) C4612](compiler-warning-level-1-c4612.md)|error en el nombre de archivo de inclusión|
|[Advertencia del compilador (nivel 1) C4613](compiler-warning-level-1-c4613.md)|'*símbolo*': no se puede cambiar la clase de segmento|
|[Advertencia del compilador (nivel 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma warning: tipo de advertencia de usuario desconocido|
|[Advertencia del compilador (nivel 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|Advertencia de #pragma: número de advertencia 'número' no es una advertencia del compilador válido|
|[Advertencia del compilador (nivel 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|parámetros de tipo pragma incluían una cadena vacía; se ha omitido pragma|
|[Advertencia del compilador (nivel 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: no existe el número de advertencia 'número'|
|[Advertencia del compilador (nivel 1) C4620](compiler-warning-level-1-c4620.md)|no se encontró ninguna forma postfija de 'operador ++' para el tipo 'tipo'; con la forma de prefijo.|
|[Advertencia del compilador (nivel 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|ninguna forma postfija de 'operator--' encontrado para el tipo 'type', con formato de prefijo|
|[Advertencia del compilador (nivel 3) C4622](compiler-warning-level-3-c4622.md)|reemplazando la información de depuración formada durante la creación del encabezado precompilado en el archivo objeto: 'file'|
|[Advertencia del compilador (nivel 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|'clase derivada': constructor predeterminado se definió implícitamente como eliminado porque un constructor predeterminado de clase base es inaccesible o se eliminó|
|[Advertencia del compilador (nivel 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|'clase derivada': destructor se definió implícitamente como eliminado porque un destructor de clase base es inaccesible o se eliminó|
|[Advertencia del compilador (nivel 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|'clase derivada': constructor de copias se definió implícitamente como eliminado porque un constructor de copias de clase base es inaccesible o se eliminó|
|[Advertencia del compilador (nivel 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|'clase derivada': operador de asignación se definió implícitamente como eliminado porque un operador de asignación de la clase base es inaccesible o se eliminó|
|[Advertencia del compilador (nivel 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<identificador >': omite al buscar el precompilado uso del encabezado|
|[Advertencia del compilador (nivel 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|los digramas no son compatibles con -Ze. Secuencia de caracteres 'digrama' no interpretado como token alternativo de '%s'|
|[Advertencia del compilador (nivel 4) C4629](compiler-warning-level-4-c4629.md)|Dígrafo usado, secuencia de caracteres 'dígrafo' interpretada como token 'char' (inserte un espacio entre los dos caracteres si no es lo que tenía previsto)|
|[Advertencia del compilador (nivel 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'símbolo': especificador de clase de almacenamiento 'extern' no es válido en la definición de miembro|
|Advertencia del compilador (nivel 2) C4631|MSXML o XPath no disponible; no se procesarán los comentarios del documento XML. reason|
|[Advertencia del compilador (nivel 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Comentario del documento XML: archivo - acceso denegado: razón|
|[Advertencia del compilador (nivel 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Destino del comentario del documento XML: error: razón|
|[Advertencia del compilador (nivel 4) C4634](compiler-warning-level-4-c4634.md)|Destino del comentario del documento XML: no se puede aplicar: motivo|
|[Advertencia del compilador (nivel 3) C4635](compiler-warning-level-3-c4635.md)|destino del comentario del documento XML: XML incorrectamente formado: motivo|
|[Advertencia del compilador (nivel 3) C4636](compiler-warning-level-3-c4636.md)|Comentario del documento XML aplicado para construir: la etiqueta requiere vacío ' atributo '.|
|[Advertencia del compilador (niveles 3 y 4) C4637](compiler-warning-level-3-c4637.md)|Destino del comentario del documento XML: \<incluyen > etiqueta descartado. Motivo|
|[Advertencia del compilador (nivel 3) C4638](compiler-warning-level-3-c4638.md)|Destino del comentario del documento XML: referencia a símbolo desconocido 'símbolo'.|
|[Advertencia del compilador (nivel 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Error MSXML, documento XML no se procesarán los comentarios. Motivo|
|[Advertencia del compilador (nivel 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instancia': la construcción del objeto estático local no es segura para subprocesos|
|[Advertencia del compilador (nivel 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Comentario del documento XML tiene una referencia cruzada ambigua:|
|[Advertencia del compilador (nivel 3) C4645](compiler-warning-level-3-c4645.md)|la función declarada con __declspec(noreturn) tiene una instrucción return|
|[Advertencia del compilador (nivel 3) C4646](compiler-warning-level-3-c4646.md)|la función declarada con __declspec(noreturn) tiene un tipo de valor devuelto distinto de void|
|Advertencia del compilador (nivel 3) C4647|cambio de comportamiento: __is_pod (*tipo*) tiene un valor diferente en las versiones anteriores|
|Advertencia del compilador (nivel 3) C4648|se omite el atributo estándar 'carries_dependency'|
|Advertencia del compilador (nivel 3) C4649|los atributos se omiten en este contexto|
|[Advertencia del compilador (nivel 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|información de depuración no está en el encabezado precompilado; solo símbolos globales del encabezado estará disponibles|
|[Advertencia del compilador (nivel 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|'definición de especificado para el encabezado precompilado pero no para la compilación actual|
|[Advertencia del compilador (nivel 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|opción del compilador 'opción' incoherente con el encabezado precompilado; la opción de línea de comandos actual invalidará la definida en el encabezado precompilado|
|[Advertencia del compilador (nivel 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|opción del compilador 'opción' incoherente con el encabezado precompilado; omitirá la opción de línea de comandos actual|
|Advertencia del compilador (nivel 4) C4654|Incluir código colocado delante del encabezado precompilado de línea se omitirá. Agregue código al encabezado precompilado.|
|[Advertencia del compilador (nivel 1) C4655](compiler-warning-level-1-c4655.md)|'símbolo': tipo de variable es nuevo desde la última compilación o se define de forma distinta en otro lugar|
|[Advertencia del compilador (nivel 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'símbolo': tipo de datos es nuevo o ha cambiado desde la última compilación o se define de forma distinta en otro lugar|
|[Advertencia del compilador (nivel 1) C4657](compiler-warning-level-1-c4657.md)|la expresión requiere a un tipo de datos que sea nuevo desde la última compilación|
|Advertencia del compilador (nivel 1) C4658|'function': prototipo de función es nuevo desde la última compilación o bien se declara de forma distinta en otro lugar|
|[Advertencia del compilador (nivel 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma 'pragma': uso del segmento reservado 'segmento' tiene un comportamiento indefinido, utilice #pragma comment (linker,...)|
|[Advertencia del compilador (nivel 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'identifier': ninguna definición adecuada proporcionada para la solicitud de creación de instancias de plantillas explícitas|
|[Advertencia del compilador (nivel 1) C4662](compiler-warning-level-1-c4662.md)|creación de instancias explícita; la clase de plantilla 'identifier1' no tiene definición a partir de la cual especializar 'identifier2'|
|[Advertencia del compilador (nivel 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'function': ninguna plantilla de función definida que coincida con creación de instancias forzada|
|[Advertencia del compilador (nivel 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'símbolo' no está definido como macro de preprocesador y se reemplaza por '0' para 'directiva'|
|[Advertencia del compilador (nivel 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'cast': conversión no segura: 'class' es un objeto de tipo administrado|
|[Advertencia del compilador (nivel 4) C4670](compiler-warning-level-4-c4670.md)|'identifier': esta clase base es inaccesible|
|Advertencia del compilador (nivel 4) C4671|'identifier': el constructor de copia es inaccesible|
|[Advertencia del compilador (nivel 4) C4672](compiler-warning-level-4-c4672.md)|'identificador1': ambiguo. Se vio primero como 'identifier2'|
|[Advertencia del compilador (nivel 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|produce los siguientes tipos de 'identifier' no se considerará en el bloque catch|
|[Advertencia del compilador (nivel 1) C4674](compiler-warning-level-1-c4674.md)|'method' se debe declarar como 'static' y tener exactamente un parámetro|
|Advertencia del compilador (nivel 4) C4676|'%s': el destructor no es accesible|
|[Advertencia del compilador (nivel 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'function': signatura de miembro no privado contiene un tipo privado de ensamblado 'tipo_privado'|
|[Advertencia del compilador (nivel 1) C4678](compiler-warning-level-1-c4678.md)|La clase base 'base_type' es menos accesible que 'derived_type'|
|[Advertencia del compilador (nivel 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'member': no se pudo importar el miembro|
|[Advertencia del compilador (nivel 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'class': coclase no especifica una interfaz predeterminada|
|[Advertencia del compilador (nivel 4) C4681](compiler-warning-level-4-c4681.md)|'class': coclase no especifica una interfaz predeterminada que sea un origen de eventos|
|[Advertencia del compilador (nivel 4) C4682](compiler-warning-level-4-c4682.md)|'parámetro': ningún parámetro direccional especificado, un atributo [in]|
|[Advertencia del compilador (nivel 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'function': origen de eventos tiene un 'out'-parámetro; Tenga cuidado al enlazar varios controladores de eventos|
|[Advertencia del compilador (nivel 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|'attribute': ADVERTENCIA!! atributo puede causar una generación de código no válido: usar con precaución|
|[Advertencia del compilador (nivel 1) C4685](compiler-warning-level-1-c4685.md)|se esperaba '> >' pero se encontró '>>' al analizar los parámetros de plantilla|
|[Advertencia del compilador (nivel 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'tipo definido por el usuario': posible cambio de comportamiento, cambio en la convención de llamada devuelta definida por el usuario|
|[Advertencia (Error) del compilador C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'class': una clase abstracta sellada no puede implementar una interfaz 'interface'|
|[Advertencia del compilador (nivel 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|'constraint': la lista de restricciones contiene un tipo privado de ensamblado 'type'|
|Advertencia del compilador (nivel 1) C4689|'%c': carácter en #pragma detect_mismatch; no admitido #pragma omitidas|
|[Advertencia del compilador (nivel 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: más elementos POP que Push|
|[Advertencia del compilador (nivel 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type': se esperaba el tipo al que hace referencia en el ensamblado sin referencia 'archivo', tipo definido en la unidad de traducción actual utilizado en su lugar|
|[Advertencia del compilador (nivel 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'función': la firma de un miembro no privado contiene un tipo nativo privado de ensamblado 'tipo_nativo'|
|[Advertencia del compilador (nivel 1, Error) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'class': una clase abstracta sellada no puede tener cualquier instancia miembros 'miembro de instancia'|
|[Advertencia del compilador (nivel 1, Error) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'class': una clase abstracta sellada no puede tener una clase base 'clase_base'|
|Advertencia del compilador (nivel 1) C4695|#pragma execution_character_set: 'el juego de caracteres' no es un argumento admitido: se admite actualmente solo "UTF-8"|
|Advertencia del compilador (nivel 1) C4696|/ Opción ZBvalue1 fuera del intervalo; Suponiendo que 'value2'|
|[Advertencia del compilador (niveles 1 y 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|variable local sin inicializar 'nombre' utilizada|
|[Advertencia del compilador (nivel 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|variable local potencialmente no inicializada 'nombre' utilizada|
|[Advertencia del compilador (nivel 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|código inaccesible|
|[Advertencia del compilador (nivel 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|variable de puntero local potencialmente no inicializada '%s' se usa|
|[Advertencia del compilador (nivel 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|asignación de la expresión condicional|
|[Advertencia del compilador (nivel 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|operador de comas dentro de la expresión de índice de matriz|
|[Advertencia del compilador (nivel 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'función': la función no está entre líneas|
|[Advertencia del compilador (nivel 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|función 'función' seleccionada para expansión automática alineada|
|[Advertencia del compilador (nivel 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|la función 'función' marcada como __forceinline no está entre línea|
|[Advertencia del compilador (nivel 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'function': no todas las rutas de acceso de control devuelven un valor|
|[Advertencia (nivel 1, Error) del compilador C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'function': debe devolver un valor|
|[Advertencia del compilador (nivel 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'function': recursiva en todas las rutas de control, función provocará el desbordamiento de pila en tiempo de ejecución|
|[Advertencia del compilador (nivel 4) C4718](compiler-warning-level-4-c4718.md)|'llamada de función': llamada recursiva no tiene efectos secundarios, eliminar|
|Advertencia del compilador (nivel 1) C4719|Al especificar Qfast - utilice 'f' como sufijo para indicar precisión sencilla se encontró una constante doble|
|Advertencia del compilador (nivel 2) C4720|informes de ensamblado en línea: 'mensaje'|
|Advertencia del compilador (nivel 1) C4721|'function': no está disponible como intrínseco|
|[Advertencia del compilador (nivel 1) C4722](compiler-warning-level-1-c4722.md)|'function': destructor nunca devuelve un valor, posible pérdida de memoria|
|[Advertencia del compilador (nivel 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|posible división por 0|
|[Advertencia del compilador (nivel 3) C4724](compiler-warning-level-3-c4724.md)|posible división (módulo) por 0|
|Advertencia del compilador (nivel 3) C4725|puede que la instrucción máquina sea incorrecta en algunos equipos Pentium|
|[Advertencia del compilador (nivel 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|PCH denominado archivo_pch con la misma marca de tiempo en archivo_obj_1 y archivo_obj_2.  Usar el primer PCH.|
|Advertencia del compilador (nivel 1) C4728|/ Opción Yl-omitida porque se requiere la referencia PCH|
|Advertencia del compilador (nivel 4) C4729|función demasiado grande para advertencias basadas en gráficos de flujos|
|[Compilador advertencia (nivel 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)advertencia del compilador (nivel 1) C4730|'main': mezcla de _m64 y expresiones pueden ocasionar código incorrecto de punto flotante|
|[Advertencia del compilador (nivel 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|'pointer': 'registro' modificado por código ensamblador en línea de registro de puntero de marco|
|Advertencia del compilador (nivel 1) C4732|intrínseco '%s' no se admite en esta arquitectura|
|[Advertencia del compilador (nivel 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Inline asm que asigna a 'FS: 0': controlador no está registrado como controlador seguro|
|[Advertencia del compilador (nivel 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento|
|[Advertencia del compilador (nivel 1) C4739](compiler-warning-level-1-c4739.md)|la referencia a la variable 'var' supera su espacio de almacenamiento|
|[Advertencia del compilador (nivel 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|flujo dentro o fuera del código inline asm suprime la optimización global|
|[Advertencia del compilador (nivel 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'var' tiene una alineación diferente en 'archivo1' y 'archivo2': número y número|
|[Advertencia del compilador (nivel 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type' tiene un tamaño diferente en 'archivo1' y 'archivo2': número y el número de bytes|
|[Advertencia del compilador (nivel 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'var' tiene un tipo diferente en 'archivo1' y 'archivo2': 'type1' y 'type2'|
|[Advertencia del compilador C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|acceso volátil de '*expresión*' está sujeta a /volatile:\<iso&#124;ms >; considere el uso de funciones intrínsecas __iso_volatile_load/store|
|[Advertencia del compilador (nivel 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Llamada administrada 'entrypoint': No se puede ejecutar código administrado en un bloqueo del cargador, incluido el DLL entrypoint y las llamadas alcanzadas desde el punto|
|Advertencia del compilador (nivel 4) C4749|condicionalmente compatible: offsetof aplicado al tipo que no son estándar diseño '*tipo*'|
|[Advertencia del compilador (nivel 1) C4750](compiler-warning-level-1-c4750.md)|'identificador': función con _alloca() insertada en un bucle|
|Advertencia del compilador (nivel 4) C4751|/ arch: AVX no es aplicable a Intel (r) extensiones SIMD de Streaming que están en ASM inline|
|Advertencia del compilador (nivel 4) C4752|encontrar extensiones de Vector avanzadas de Intel (r); Considere el uso de/arch: AVX|
|[Advertencia del compilador (nivel 4) C4754](compiler-warning-level-4-c4754.md)|Las reglas de conversión para las operaciones aritméticas en la comparación de %s(%d) significan que una bifurcación no puede ejecutarse. Convertir '%s' a '%s' (o un tipo similar de %d bytes).|
|Advertencia C4755 del compilador|Las reglas de conversión para las operaciones aritméticas en la comparación de %s(%d) significan que una bifurcación no puede ejecutarse en una función inline. Convertir '%s' a '%s' (o un tipo similar de %d bytes).|
|[Advertencia del compilador (nivel 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|desbordamiento en la aritmética de constante|
|Advertencia del compilador (nivel 4) C4757|el subíndice es un valor grande sin signo, ¿realmente pensaba en una constante negativa?|
|[Advertencia del compilador (nivel 4) C4764](compiler-warning-level-4-c4764.md)|No se pueden alinear objetos detectados con elementos mayores de 16 bytes|
|Advertencia del compilador (nivel 4) C4767|nombre de sección '%s' tiene más de 8 caracteres y se truncará el vinculador|
|Advertencia del compilador (nivel 3) C4768|se omiten los atributos __declspec anteriores a la especificación de vinculación|
|Advertencia C4770 del compilador|valida parcialmente enum '*nombre*' utilizar como índice|
|Advertencia C4771 del compilador|Los límites se deben crear con un puntero simple; MPX intrínseca que se ignorará|
|[Del compilador (nivel 1, Error) de la advertencia C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import hace referencia a un tipo de una biblioteca de tipos que faltan; 'falta_tipo' como marcador de posición|
|Advertencia del compilador (nivel 4) C4774|'*cadena*': se esperaba en el argumento de cadena de formato *número* no es literal de cadena|
|Advertencia del compilador (nivel 3) C4775|ha utilizado una extensión en la cadena de formato '*cadena*'de la función'*función*'|
|Advertencia del compilador (nivel 1) C4776|' %*carácter*'no se permite en la cadena de formato de la función'*función*'|
|Advertencia del compilador (nivel 4) C4777|'*función*': cadena de formato '*cadena*'requiere un argumento de tipo'*type1*', pero el argumento variádico *número* tiene el tipo '*type2*'|
|Advertencia del compilador (nivel 3) C4778|'*función*': sin terminar la cadena de formato '*cadena*'|
|[Advertencia del compilador (nivel 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'identifier': identificador se ha truncado a 'número' caracteres|
|[Advertencia del compilador (nivel 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|se producirá una saturación del búfer 'identificador' con un tamaño de N bytes; se escribirán M bytes empezando en el desplazamiento L|
|Advertencia del compilador (nivel 2) C4792|la función '%s' declarada usando sysimport a hacer referencia desde código nativo; biblioteca de importación requerida para vincular|
|[Advertencia del compilador (niveles 1 y 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'function': función compilada como nativa: \n\t'reason'|
|[Advertencia del compilador (nivel 1) C4794](compiler-warning-level-1-c4794.md)|segmento de almacenamiento local de subprocesos de variable '%s' cambiado de '%s' a '%s'|
|[Advertencia del compilador (nivel 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|la función 'función' tiene una instrucción máquina EMMS|