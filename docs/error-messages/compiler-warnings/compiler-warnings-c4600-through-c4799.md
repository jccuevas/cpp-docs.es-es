---
title: C4600 de advertencias del compilador a través de C4799 | Documentos de Microsoft
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4602
- C4603
- C4609
- C4612
- C4613
- C4620
- C4622
- C4629
- C4631
- C4634
- C4635
- C4636
- C4637
- C4638
- C4645
- C4646
- C4655
- C4657
- C4658
- C4662
- C4670
- C4671
- C4672
- C4674
- C4676
- C4678
- C4681
- C4682
- C4685
- C4688
- C4689
- C4690
- C4693
- C4694
- C4695
- C4696
- C4718
- C4719
- C4720
- C4721
- C4722
- C4724
- C4725
- C4728
- C4729
- C4732
- C4739
- C4750
- C4751
- C4752
- C4754
- C4755
- C4757
- C4764
- C4767
- C4770
- C4792
- C4794
dev_langs:
- C++
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad29989e89bfe60f2180ee48c411ebd4d3098ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warnings-c4600-through-c4799"></a>C4600 de advertencias del compilador a través de C4799

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de advertencia generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Mensajes de advertencia

|Advertencia|Mensaje|
|-------------|-------------|
|[Advertencia del compilador (nivel 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma 'macro name': se esperaba una cadena no vacía válida|
|Advertencia del compilador (nivel 1) C4602|#pragma pop_macro: 'macro name' ninguna #pragma push_macro anterior para este identificador|
|Advertencia del compilador (nivel 1) C4603|'*identificador*': no se definió la macro o la definición es diferente después del uso del encabezado precompilado|
|Advertencia del compilador (nivel 1) C4604|'*tipo*': pasar argumentos por valor a través de límites nativo y administrado requiere el constructor de copias válido. En caso contrario, el comportamiento de tiempo de ejecución es indefinido|
|Advertencia del compilador (nivel 1) C4605|' /D*macro*' especificado en la línea de comandos actual, pero no se especificó cuando se creó el encabezado precompilado|
|[Advertencia del compilador (nivel 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|Advertencia de #pragma: 'número de advertencia' omitida; Advertencias de análisis de código no están asociadas con niveles de advertencia|
|[Advertencia del compilador (nivel 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|“union_member” ya ha sido inicializado por otro miembro union en la lista de inicializadores, “union_member”|
|Advertencia del compilador (nivel 3, Error) C4609|'*type1*'que se deriva de la interfaz predeterminada'*interfaz*'de tipo'*type2*'. Usar una interfaz predeterminada distinta de '*type1*', o romper la relación de base/derivada.|
|[Advertencia del compilador (nivel 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|nunca se puede crear instancias de objeto 'clase': se requiere un constructor definido por el usuario|
|[Advertencia del compilador (nivel 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|interacción entre 'función' y la destrucción de objetos de C++ es no portable|
|Advertencia del compilador (nivel 1) C4612|error en el nombre de archivo de inclusión|
|Advertencia del compilador (nivel 1) C4613|'*símbolo*': no se puede cambiar la clase de segmento|
|[Advertencia del compilador (nivel 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma warning: tipo de advertencia de usuario desconocido|
|[Advertencia del compilador (nivel 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma warning: número de advertencia 'número' no es una advertencia válida del compilador|
|[Advertencia del compilador (nivel 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|parámetros de tipo pragma incluían una cadena vacía; se ha omitido pragma|
|[Advertencia del compilador (nivel 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: no existe el número de advertencia 'número'|
|Advertencia del compilador (nivel 1) C4620|no se encontró ninguna forma postfija de 'operador ++' para el tipo 'tipo'; con la forma de prefijo.|
|[Advertencia del compilador (nivel 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|ninguna forma postfija de 'operator': se encontró para el tipo 'tipo', con formato de prefijo|
|Advertencia del compilador (nivel 3) C4622|reemplazando la información de depuración formada durante la creación del encabezado precompilado en el archivo objeto: 'archivo'|
|[Advertencia del compilador (nivel 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|'clase derivada': constructor predeterminado se definió implícitamente como eliminado porque un constructor predeterminado de clase base es inaccesible o se ha eliminado|
|[Advertencia del compilador (nivel 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|'clase derivada': destructor se definió implícitamente como eliminado porque un destructor de clase base es inaccesible o se ha eliminado|
|[Advertencia del compilador (nivel 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|'clase derivada': constructor de copias se definió implícitamente como eliminado porque un constructor de copias de clase base es inaccesible o se ha eliminado|
|[Advertencia del compilador (nivel 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|'clase derivada': el operador de asignación se definió implícitamente como eliminado porque un operador de asignación de la clase base es inaccesible o se ha eliminado|
|[Advertencia del compilador (nivel 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<identificador >': omite al buscar el precompilado uso del encabezado|
|[Advertencia del compilador (nivel 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|los digramas no son compatibles con -Ze. Secuencia de caracteres 'digrama' no interpretado como token alternativo de '%s'|
|Advertencia del compilador (nivel 4) C4629|Dígrafo usado, secuencia de caracteres 'dígrafo' interpretada como token 'char' (inserte un espacio entre los dos caracteres si no es lo que tenía previsto)|
|[Advertencia del compilador (nivel 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'símbolo': especificador de clase de almacenamiento 'extern' no es válido para la definición de miembro|
|Advertencia del compilador (nivel 2) C4631|MSXML o XPath no disponible; no se procesarán los comentarios del documento XML. reason|
|[Advertencia del compilador (nivel 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Comentario del documento XML: archivo - acceso denegado: razón|
|[Advertencia del compilador (nivel 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Destino del comentario de documento XML: error: razón|
|Advertencia del compilador (nivel 4) Advertencia C4634|Destino del comentario de documento XML: no se puede aplicar: motivo|
|Advertencia del compilador (nivel 3) C4635|destino del comentario del documento XML: XML incorrectamente formado: motivo|
|Advertencia del compilador (nivel 3) C4636|Comentario del documento XML aplicado a construcción: etiqueta requiere non empty 'atributo ' atributo '.|
|Advertencia del compilador (nivel 3 y nivel 4) C4637|Destino del comentario de documento XML: \<incluyen > etiqueta descartada. Motivo|
|Advertencia del compilador (nivel 3) C4638|Destino del comentario de documento XML: referencia a símbolo desconocido 'símbolo'.|
|[Advertencia del compilador (nivel 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Error MSXML, no se procesarán comentarios de documento XML. Motivo|
|[Advertencia del compilador (nivel 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instancia': la construcción del objeto estático local no es segura para subprocesos|
|[Advertencia del compilador (nivel 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Comentario del documento XML tiene una referencia cruzada ambigua:|
|Advertencia del compilador (nivel 3) C4645|la función declarada con __declspec(noreturn) tiene una instrucción return|
|Advertencia del compilador (nivel 3) C4646|la función declarada con __declspec(noreturn) tiene un tipo de valor devuelto distinto de void|
|Advertencia del compilador (nivel 3) C4647|cambio de comportamiento: __is_pod (*tipo*) tiene un valor diferente en las versiones anteriores|
|Advertencia del compilador (nivel 3) C4648|se omite el atributo estándar 'carries_dependency'|
|Advertencia del compilador (nivel 3) C4649|se omiten los atributos en este contexto|
|[Advertencia del compilador (nivel 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|información de depuración no está en el encabezado precompilado; solo los símbolos globales del encabezado estará disponibles|
|[Advertencia del compilador (nivel 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|'definición de especificado para el encabezado precompilado pero no para la compilación actual|
|[Advertencia del compilador (nivel 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|opción del compilador 'opción' no es coherente con el encabezado precompilado; opción de línea de comandos actual invalidará la definida en el encabezado precompilado|
|[Advertencia del compilador (nivel 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|opción del compilador 'opción' no es coherente con el encabezado precompilado; omitidas la opción de línea de comandos actual|
|Advertencia del compilador (nivel 4) C4654|Incluir código se coloca antes del encabezado precompilado se pasará por alto de línea. Agregue código al encabezado precompilado.|
|Advertencia del compilador (nivel 1) C4655|'símbolo': tipo de variable es nuevo desde la última compilación o se define de forma diferente en otra ubicación|
|[Advertencia del compilador (nivel 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'símbolo': tipo de datos es nueva o ha cambiado desde la última compilación o se define de forma diferente en otra ubicación|
|Advertencia del compilador (nivel 1) C4657|la expresión requiere a un tipo de datos que sea nuevo desde la última compilación|
|Advertencia del compilador (nivel 1) C4658|'función': prototipo de función es nuevo desde la última compilación o se declara de forma diferente en otra ubicación|
|[Advertencia del compilador (nivel 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma 'pragma': uso del segmento reservado 'segmento' tiene un comportamiento indefinido, utilice #pragma comment (linker,...)|
|[Advertencia del compilador (nivel 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'identificador': ninguna definición adecuada proporcionada para la solicitud de creación de instancias de plantilla explícitos|
|Advertencia del compilador (nivel 1) C4662|creación de instancias explícita; la clase de plantilla 'identifier1' no tiene definición a partir de la cual especializar 'identifier2'|
|[Advertencia del compilador (nivel 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'función': ninguna función definida por la plantilla que coincida con fuerza la creación de instancias|
|[Advertencia del compilador (nivel 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'símbolo' no está definido como macro de preprocesador y se reemplaza por '0' para 'directiva'|
|[Advertencia del compilador (nivel 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'conversión': conversión no segura: 'clase' es un objeto de tipo administrado|
|Advertencia del compilador (nivel 4) C4670|'identificador': esta clase base es inaccesible|
|Advertencia del compilador (nivel 4) C4671|'identificador': el constructor de copias no es accesible|
|Advertencia del compilador (nivel 4) C4672|'identificador1': ambiguo. Se vio primero como 'identifier2'|
|[Advertencia del compilador (nivel 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|produce los siguientes tipos de 'identifier' no se considerarán en el bloque catch|
|Advertencia del compilador (nivel 1) Advertencia C4674|'method' se debe declarar como 'static' y tener exactamente un parámetro|
|Advertencia del compilador (nivel 4) C4676|'%s': el destructor no es accesible|
|[Advertencia del compilador (nivel 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'función': la firma de un miembro no privado contiene un tipo privado de ensamblado 'tipo_privado'|
|Advertencia del compilador (nivel 1) C4678|La clase base 'base_type' es menos accesible que 'derived_type'|
|[Advertencia del compilador (nivel 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'member': no se pudo importar el miembro|
|[Advertencia del compilador (nivel 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'class': coclase no especifica una interfaz predeterminada|
|Advertencia del compilador (nivel 4) C4681|'class': coclase no especifica una interfaz predeterminada que sea un origen de eventos|
|Advertencia del compilador (nivel 4) C4682|'parámetro': parámetro direccional se especificó ningún atributo, el valor predeterminado [in]|
|[Advertencia del compilador (nivel 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'función': origen de eventos tiene un 'out': parámetro; Tenga cuidado al enlazar varios controladores de eventos|
|[Advertencia del compilador (nivel 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|'atributo': advertencia!! atributo puede causar una generación de código no válido: usar con precaución|
|Advertencia del compilador (nivel 1) C4685|se esperaba '> >' pero se encontró '>>' al analizar los parámetros de plantilla|
|[Advertencia del compilador (nivel 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'tipo definido por el usuario': posible cambio de comportamiento, cambio en la convención de llamada devuelta definida por el usuario|
|[Advertencia (Error) del compilador C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'clase': una clase abstracta sealed no puede implementar una interfaz 'interfaz'|
|Advertencia del compilador (nivel 1) C4688|'constraint': la lista de restricciones contiene un tipo privado de ensamblado 'type'|
|Advertencia del compilador (nivel 1) C4689|'%c': no se admite caracteres de #pragma detect_mismatch; #pragma omitidas|
|Advertencia del compilador (nivel 4) C4690|[ emitidl ( pop ) ]: más elementos POP que Push|
|[Advertencia del compilador (nivel 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type': se esperaba el tipo al que hace referencia en el ensamblado sin referencia 'archivo', tipo definido en la unidad de traducción actual utilizado en su lugar|
|[Advertencia del compilador (nivel 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'función': la firma de un miembro no privado contiene un tipo nativo privado de ensamblado 'tipo_nativo'|
|[Advertencia del compilador (nivel 1, Error) Advertencia C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'clase': una clase abstracta sealed no puede tener cualquier instancia de 'miembro de instancia' miembros|
|[Advertencia del compilador (nivel 1, Error) Advertencia C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'clase': una clase abstracta sealed no puede tener una clase base 'clase_base'|
|Advertencia del compilador (nivel 1) C4695|#pragma execution_character_set: 'juego de caracteres' no es un argumento admitido: se admite actualmente solo 'UTF-8'|
|Advertencia del compilador (nivel 1) C4696|/ Opción ZBvalue1 fuera del intervalo; Suponiendo que 'value2'|
|[Advertencia del compilador (niveles 1 y 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|variable local no inicializada 'nombre' utilizada|
|[Advertencia del compilador (nivel 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|variable local potencialmente no inicializada 'nombre' utilizada|
|[Advertencia del compilador (nivel 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|código inalcanzable|
|[Advertencia del compilador (nivel 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|variable de puntero local potencialmente no inicializada '%s' utiliza|
|[Advertencia del compilador (nivel 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|asignación en la expresión condicional|
|[Advertencia del compilador (nivel 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|operador de coma en la expresión de índice de matriz|
|[Advertencia del compilador (nivel 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'función': la función no está entre líneas|
|[Advertencia del compilador (nivel 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|función 'función' seleccionada para expansión en línea automática|
|[Advertencia del compilador (nivel 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|la función 'función' marcada como __forceinline no está entre línea|
|[Advertencia del compilador (nivel 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'función': no todas las rutas de acceso de control devuelven un valor|
|[Compilador advertencia (nivel 1, Error) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'función': debe devolver un valor|
|[Advertencia del compilador (nivel 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'función': recursiva en todas las rutas de control, función hará que el desbordamiento de pila en tiempo de ejecución|
|Advertencia del compilador (nivel 4) C4718|'llamada de función': llamada recursiva no tiene efectos secundarios, eliminar|
|Advertencia del compilador (nivel 1) C4719|Al especificar Qfast - utilice 'f' como sufijo para indicar precisión simple se encontró una constante doble|
|Advertencia del compilador (nivel 2) C4720|informes de ensamblador en línea: 'mensaje'|
|Advertencia del compilador (nivel 1) C4721|'función': no disponible como función intrínseca|
|Advertencia del compilador (nivel 1) C4722|'función': destructor nunca devuelve un valor, posible pérdida de memoria|
|[Advertencia del compilador (nivel 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|posible división por 0|
|Advertencia del compilador (nivel 3) C4724|posible división (módulo) por 0|
|Advertencia del compilador (nivel 3) C4725|puede que la instrucción máquina sea incorrecta en algunos equipos Pentium|
|[Advertencia del compilador (nivel 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|PCH denominado archivo_pch con la misma marca de tiempo en archivo_obj_1 y archivo_obj_2.  Uso de primer PCH.|
|Advertencia del compilador (nivel 1) C4728|/ Yl-(opción) pasa por alto porque se requiere la referencia de PCH|
|Advertencia del compilador (nivel 4) C4729|función demasiado grande para advertencias basadas en gráficos de flujos|
|[Compilador advertencia (nivel 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)advertencia del compilador (nivel 1) C4730|'main': mezcla de _m64 y expresiones pueden derivar en código incorrecto de punto flotante|
|[Advertencia del compilador (nivel 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|'pointer': 'registro' modificado por código ensamblador en línea de registro de puntero de marco|
|Advertencia del compilador (nivel 1) C4732|función intrínseca '%s' no se admite en esta arquitectura|
|[Advertencia del compilador (nivel 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Inline asm que asigna a 'FS: 0': controlador no está registrado como controlador seguro|
|[Advertencia del compilador (nivel 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento|
|Advertencia del compilador (nivel 1) C4739|la referencia a la variable 'var' supera su espacio de almacenamiento|
|[Advertencia del compilador (nivel 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|flujo de dentro o fuera de código inline asm suprime la optimización global|
|[Advertencia del compilador (nivel 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'var' tiene una alineación diferente en 'archivo1' y 'archivo2': número y número|
|[Advertencia del compilador (nivel 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type' tiene un tamaño diferente en 'archivo1' y 'archivo2': número y el número de bytes|
|[Advertencia del compilador (nivel 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'var' tiene un tipo diferente en 'archivo1' y 'archivo2': 'type1' y 'type2'|
|[Advertencia del compilador C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|acceso volátil de '*expresión*' está sujeta a /volatile:\<iso&#124;ms > establecer; considere el uso de funciones intrínsecas de __iso_volatile_load/almacén|
|[Advertencia del compilador (nivel 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Al llamar a 'entrypoint' administrado: no se puede ejecutar código administrado en un bloqueo del cargador, incluido el punto de entrada DLL y las llamadas alcanzadas desde el punto de entrada DLL|
|Advertencia del compilador (nivel 4) C4749|admite condicionalmente: offsetof aplicado al tipo de diseño de standard sin '*tipo*'|
|Advertencia del compilador (nivel 1) C4750|'identificador': función con _alloca() insertada en un bucle|
|Advertencia del compilador (nivel 4) C4751|/ arch: AVX no se aplica a Intel (r) extensiones SIMD de Streaming que están dentro de inline ASM|
|Advertencia del compilador (nivel 4) C4752|se encontró extensiones de Vector avanzadas de Intel (r); Considere el uso de/arch: AVX|
|Advertencia del compilador (nivel 4) C4754|Las reglas de conversión para las operaciones aritméticas de la comparación en %s(%d) significan que una bifurcación no se puede ejecutar. Convierte '%s' en '%s' (o un tipo similar de %d bytes).|
|C4755 de advertencia del compilador|Las reglas de conversión para las operaciones aritméticas de la comparación en %s(%d) significan que una bifurcación no puede ejecutarse en una función insertada. Convierte '%s' en '%s' (o un tipo similar de %d bytes).|
|[Advertencia del compilador (nivel 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|desbordamiento en aritmética de constante|
|Advertencia del compilador (nivel 4) C4757|es un valor sin signo grande, ¿deseaba una constante negativa?|
|Advertencia del compilador (nivel 4) C4764|No se pueden alinear objetos detectados con elementos mayores de 16 bytes|
|Advertencia del compilador (nivel 4) C4767|nombre de sección '%s' es superior a 8 caracteres y se truncará el vinculador|
|Advertencia del compilador (nivel 3) C4768|se omiten los atributos __declspec antes de la especificación de vinculación|
|C4770 de advertencia del compilador|valida parcialmente enum '*nombre*' usa como índice|
|C4771 de advertencia del compilador|Límites deben crearse mediante un puntero simple; Función intrínseca MPX omitida|
|[Compilador (nivel 1, Error) de la advertencia C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import hace referencia a un tipo de una biblioteca de tipos que falta; 'falta_tipo' como marcador de posición|
|Advertencia del compilador (nivel 4) C4774|'*cadena*': se esperaba en un argumento de una cadena de formato *número* no es literal de cadena|
|Advertencia del compilador (nivel 3) C4775|extensión no estándar utilizada en la cadena de formato '*cadena*'de la función'*función*'|
|Advertencia del compilador (nivel 1) C4776|' %*caracteres*'no se permite en la cadena de formato de la función'*función*'|
|Advertencia del compilador (nivel 4) C4777|'*función*': cadena de formato '*cadena*'requiere un argumento de tipo'*type1*', pero el argumento variádicas *número* tiene el tipo '*type2*'|
|Advertencia del compilador (nivel 3) C4778|'*función*': terminada la cadena de formato '*cadena*'|
|[Advertencia del compilador (nivel 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'identificador': identificador se ha truncado a 'número' caracteres|
|[Advertencia del compilador (nivel 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|se producirá una saturación del búfer 'identificador' con un tamaño de N bytes; se escribirán M bytes empezando en el desplazamiento L|
|Advertencia del compilador (nivel 2) C4792|función '%s' declarada usando sysimport a hace referencia desde código nativo; biblioteca de importación necesaria para vincular|
|[Advertencia del compilador (niveles 1 y 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'función': función compilada como nativa: \n\t'reason'|
|Advertencia del compilador (nivel 1) C4794|segmento de variable '%s' ha cambiado de '%s' a '%s' de almacenamiento local de subprocesos|
|[Advertencia del compilador (nivel 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|función 'función' no tiene ninguna instrucción EMMS|