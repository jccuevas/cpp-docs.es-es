---
title: Advertencias del compilador de C4600 a C4799
ms.date: 04/21/2019
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
- C4728
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
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 638af32b27f8d66086f3a39b74ecd46fdbb4649d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438174"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>Advertencias del compilador de C4600 a C4799

En los artículos de esta sección de la documentación se explica un subconjunto de los mensajes de advertencia generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Mensajes de advertencia

|Advertencia|Message|
|-------------|-------------|
|[ADVERTENCIA del compilador (nivel 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma ' macro name ': se esperaba una cadena no vacía válida|
|[ADVERTENCIA del compilador (nivel 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: ' macro name ' no hay ningún push_macro de #pragma anterior para este identificador|
|[ADVERTENCIA del compilador (nivel 1) C4603](compiler-warning-level-1-c4603.md)|'*Identifier*': la macro no está definida o la definición es diferente después del uso del encabezado precompilado|
|ADVERTENCIA del compilador (nivel 1) C4604|'*Type*': pasar argumentos por valor a través de un límite nativo y administrado requiere un constructor de copia válido. En caso contrario, el comportamiento en tiempo de ejecución es indefinido|
|ADVERTENCIA del compilador (nivel 1) C4605|'/D*macro*' especificada en la línea de comandos actual, pero no se especificó cuando se compiló el encabezado precompilado|
|[ADVERTENCIA del compilador (nivel 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma ADVERTENCIA: se omitió ' número de advertencia '; Las advertencias de análisis de código no están asociadas a los niveles de advertencia|
|[ADVERTENCIA del compilador (nivel 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|“union_member” ya ha sido inicializado por otro miembro union en la lista de inicializadores, “union_member”|
|ADVERTENCIA del compilador (nivel 3, error) C4609|'*tipo1*' deriva de la interfaz predeterminada '*interface*' en el tipo '*Type2*'. Use una interfaz predeterminada diferente para '*tipo1*' o divida la relación base/derivada.|
|[ADVERTENCIA del compilador (nivel 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|nunca se puede crear una instancia del objeto ' Class ': se requiere un constructor definido por el usuario|
|[ADVERTENCIA del compilador (nivel 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|la interacción entre ' función ' C++ y la destrucción de objetos no es portátil|
|[ADVERTENCIA del compilador (nivel 1) C4612](compiler-warning-level-1-c4612.md)|error en el nombre de archivo de inclusión|
|[ADVERTENCIA del compilador (nivel 1) C4613](compiler-warning-level-1-c4613.md)|'*Symbol*': no se puede cambiar la clase de segmento|
|[ADVERTENCIA del compilador (nivel 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|ADVERTENCIA de #pragma: tipo de advertencia de usuario desconocido|
|[ADVERTENCIA del compilador (nivel 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma ADVERTENCIA: el número de advertencia ' número ' no es una advertencia de compilador válida|
|[ADVERTENCIA del compilador (nivel 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|los parámetros de pragma incluyen una cadena vacía; pragma omitida|
|[ADVERTENCIA del compilador (nivel 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: no existe el número de advertencia 'número'|
|[ADVERTENCIA del compilador (nivel 1) C4620](compiler-warning-level-1-c4620.md)|no se encontró ninguna forma postfija de 'operador ++' para el tipo 'tipo'; con la forma de prefijo.|
|[ADVERTENCIA del compilador (nivel 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|no se encontró ninguna forma postfija de ' Operator--' para el tipo ' type ', con el formato de prefijo|
|[ADVERTENCIA del compilador (nivel 3) C4622](compiler-warning-level-3-c4622.md)|sobrescribiendo la información de depuración formada durante la creación del encabezado precompilado en el archivo objeto: ' file '|
|[ADVERTENCIA del compilador (nivel 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|' clase derivada ': el constructor predeterminado se definió implícitamente como eliminado porque un constructor predeterminado de clase base es inaccesible o se ha eliminado|
|[ADVERTENCIA del compilador (nivel 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|' clase derivada ': el destructor se definió implícitamente como eliminado porque un destructor de clase base es inaccesible o se ha eliminado|
|[ADVERTENCIA del compilador (nivel 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|' clase derivada ': el constructor de copia se definió implícitamente como eliminado porque un constructor de copias de clase base es inaccesible o se ha eliminado|
|[ADVERTENCIA del compilador (nivel 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|' clase derivada ': el operador de asignación se definió implícitamente como eliminado porque un operador de asignación de clase base es inaccesible o se ha eliminado|
|[ADVERTENCIA del compilador (nivel 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<identificador > ': se omite al buscar el uso del encabezado precompilado|
|[ADVERTENCIA del compilador (nivel 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|los digramas no son compatibles con -Ze. La secuencia de caracteres ' dígrafo ' no se interpreta como token alternativo para '% s '|
|[ADVERTENCIA del compilador (nivel 4) C4629](compiler-warning-level-4-c4629.md)|Dígrafo usado, secuencia de caracteres 'dígrafo' interpretada como token 'char' (inserte un espacio entre los dos caracteres si no es lo que tenía previsto)|
|[ADVERTENCIA del compilador (nivel 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|' Symbol ': el especificador de clase de almacenamiento ' extern ' no es válido en la definición de miembro|
|ADVERTENCIA del compilador (nivel 2) C4631|MSXML o XPath no disponible; no se procesarán los comentarios del documento XML. reason|
|[ADVERTENCIA del compilador (nivel 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Comentario del documento XML: acceso al archivo denegado: motivo|
|[ADVERTENCIA del compilador (nivel 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Destino del comentario del documento XML: error: motivo|
|[ADVERTENCIA del compilador (nivel 4) C4634](compiler-warning-level-4-c4634.md)|Destino del comentario del documento XML: no se puede aplicar: motivo|
|[ADVERTENCIA del compilador (nivel 3) C4635](compiler-warning-level-3-c4635.md)|destino del comentario del documento XML: XML incorrectamente formado: motivo|
|[ADVERTENCIA del compilador (nivel 3) C4636](compiler-warning-level-3-c4636.md)|Comentario del documento XML aplicado a la construcción: la etiqueta requiere un atributo ' Attribute ' que no esté vacío.|
|[ADVERTENCIA del compilador (nivel 3 y nivel 4) C4637](compiler-warning-level-3-c4637.md)|Destino del comentario del documento XML: \<incluir > etiqueta descartada. Motivo|
|[ADVERTENCIA del compilador (nivel 3) C4638](compiler-warning-level-3-c4638.md)|Destino del comentario del documento XML: referencia a símbolo desconocido ' símbolo '.|
|[ADVERTENCIA del compilador (nivel 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Error de MSXML, no se procesarán los comentarios del documento XML. Motivo|
|[ADVERTENCIA del compilador (nivel 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instancia': la construcción del objeto estático local no es segura para subprocesos|
|[ADVERTENCIA del compilador (nivel 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|El comentario del documento XML tiene una referencia cruzada ambigua:|
|[ADVERTENCIA del compilador (nivel 3) C4645](compiler-warning-level-3-c4645.md)|la función declarada con __declspec(noreturn) tiene una instrucción return|
|[ADVERTENCIA del compilador (nivel 3) C4646](compiler-warning-level-3-c4646.md)|la función declarada con __declspec(noreturn) tiene un tipo de valor devuelto distinto de void|
|ADVERTENCIA del compilador (nivel 3) C4647|cambio de comportamiento: __is_pod (*tipo*) tiene un valor diferente en versiones anteriores|
|ADVERTENCIA del compilador (nivel 3) C4648|se omite el atributo estándar ' carries_dependency '|
|ADVERTENCIA del compilador (nivel 3) C4649|los atributos se omiten en este contexto|
|[ADVERTENCIA del compilador (nivel 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|la información de depuración no está en el encabezado precompilado; solo estarán disponibles los símbolos globales del encabezado|
|[ADVERTENCIA del compilador (nivel 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|' Definition ' especificado para el encabezado precompilado, pero no para la compilación actual|
|[ADVERTENCIA del compilador (nivel 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|opción del compilador ' opción ' incoherente con el encabezado precompilado; la opción de línea de comandos actual invalidará que se define en el encabezado precompilado|
|[ADVERTENCIA del compilador (nivel 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|opción del compilador ' opción ' incoherente con el encabezado precompilado; se omitió la opción de línea de comandos actual|
|ADVERTENCIA del compilador (nivel 4) C4654|Se omitirá el código colocado antes de incluir la línea del encabezado precompilado. Agregue código al encabezado precompilado.|
|[ADVERTENCIA del compilador (nivel 1) C4655](compiler-warning-level-1-c4655.md)|' Symbol ': el tipo de variable es nuevo desde la última compilación o bien se ha definido de forma distinta en otro lugar|
|[ADVERTENCIA del compilador (nivel 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|' Symbol ': el tipo de datos es nuevo o ha cambiado desde la última compilación o bien se ha definido de forma distinta en otro lugar|
|[ADVERTENCIA del compilador (nivel 1) C4657](compiler-warning-level-1-c4657.md)|la expresión requiere un tipo de datos que sea nuevo desde la última compilación|
|ADVERTENCIA del compilador (nivel 1) C4658|' función ': el prototipo de función es nuevo desde la última compilación o se ha declarado de forma distinta en otro lugar|
|[ADVERTENCIA del compilador (nivel 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma ' pragma ': el uso del segmento reservado ' Segment ' tiene un comportamiento indefinido, use #pragma Comentario (linker,...)|
|[ADVERTENCIA del compilador (nivel 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|' Identifier ': no se proporcionó una definición adecuada para la solicitud de creación de instancias de plantilla explícita|
|[ADVERTENCIA del compilador (nivel 1) C4662](compiler-warning-level-1-c4662.md)|creación de instancias explícita; la clase de plantilla 'identifier1' no tiene definición a partir de la cual especializar 'identifier2'|
|[ADVERTENCIA del compilador (nivel 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|' función ': no hay ninguna plantilla de función definida que coincida con la creación de instancias forzada|
|[ADVERTENCIA del compilador (nivel 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|' Symbol ' no está definido como una macro de preprocesador y se reemplaza por ' 0 ' para ' Directiva '|
|[ADVERTENCIA del compilador (nivel 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|' Cast ': conversión no segura: ' Class ' es un objeto de tipo administrado|
|[ADVERTENCIA del compilador (nivel 4) C4670](compiler-warning-level-4-c4670.md)|' Identifier ': no se puede obtener acceso a esta clase base|
|ADVERTENCIA del compilador (nivel 4) C4671|' Identifier ': no se puede obtener acceso al constructor de copias|
|[ADVERTENCIA del compilador (nivel 4) C4672](compiler-warning-level-4-c4672.md)|' identificador1 ': ambiguo. Se vio primero como 'identifier2'|
|[ADVERTENCIA del compilador (nivel 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|al iniciar ' Identifier ', los siguientes tipos no se tendrán en cuenta en el sitio Catch|
|[ADVERTENCIA del compilador (nivel 1) C4674](compiler-warning-level-1-c4674.md)|'method' se debe declarar como 'static' y tener exactamente un parámetro|
|ADVERTENCIA del compilador (nivel 4) C4676|'% s ': no se puede obtener acceso al destructor|
|[ADVERTENCIA del compilador (nivel 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|' función ': la signatura de un miembro no privado contiene un tipo privado de ensamblado ' private_type '|
|[ADVERTENCIA del compilador (nivel 1) C4678](compiler-warning-level-1-c4678.md)|La clase base 'base_type' es menos accesible que 'derived_type'|
|[ADVERTENCIA del compilador (nivel 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|' Member ': no se pudo importar el miembro|
|[ADVERTENCIA del compilador (nivel 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|' Class ': la coclase no especifica una interfaz predeterminada|
|[ADVERTENCIA del compilador (nivel 4) C4681](compiler-warning-level-4-c4681.md)|' Class ': la coclase no especifica una interfaz predeterminada que sea un origen de eventos|
|[ADVERTENCIA del compilador (nivel 4) C4682](compiler-warning-level-4-c4682.md)|' parámetro ': no se especificó ningún atributo de parámetro direccional; el valor predeterminado es [in]|
|[ADVERTENCIA del compilador (nivel 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|' función ': el origen del evento tiene un parámetro ' out' '; Tenga cuidado al enlazar varios controladores de eventos|
|[ADVERTENCIA del compilador (nivel 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|' atributo ': ADVERTENCIA!! el atributo puede producir una generación de código no válida: use con precaución|
|[ADVERTENCIA del compilador (nivel 1) C4685](compiler-warning-level-1-c4685.md)|se esperaba '> >' pero se encontró '>>' al analizar los parámetros de plantilla|
|[ADVERTENCIA del compilador (nivel 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'tipo definido por el usuario': posible cambio de comportamiento, cambio en la convención de llamada devuelta definida por el usuario|
|[ADVERTENCIA del compilador (error) C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|' Class ': una clase abstracta sellada no puede implementar una interfaz ' interface '|
|[ADVERTENCIA del compilador (nivel 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|'constraint': la lista de restricciones contiene un tipo privado de ensamblado 'type'|
|ADVERTENCIA del compilador (nivel 1) C4689|'% c ': carácter no admitido en #pragma detect_mismatch; #pragma omitido|
|[ADVERTENCIA del compilador (nivel 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: más pop que las inserciones|
|[ADVERTENCIA del compilador (nivel 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|' type ': se esperaba el tipo al que se hace referencia en el ensamblado ' file ' sin referencia, tipo definido en la unidad de traducción actual que se usa en su lugar|
|[ADVERTENCIA del compilador (nivel 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'función': la firma de un miembro no privado contiene un tipo nativo privado de ensamblado 'tipo_nativo'|
|[ADVERTENCIA del compilador (nivel 1, error) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|' Class ': una clase abstracta sellada no puede tener miembros de instancia ' instance Member '|
|[ADVERTENCIA del compilador (nivel 1, error) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|' Class ': una clase abstracta sellada no puede tener una clase base ' base_class '|
|ADVERTENCIA del compilador (nivel 1) C4695|#pragma execution_character_set: ' juego de caracteres ' no es un argumento admitido: actualmente solo se admite ' UTF-8 '|
|ADVERTENCIA del compilador (nivel 1) C4696|Opción de/ZBvalue1 fuera del intervalo; Suponiendo ' valor2 '|
|[ADVERTENCIA del compilador (nivel 1 y nivel 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|se usó la variable local ' name ' sin inicializar|
|[ADVERTENCIA del compilador (nivel 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|no se ha inicializado la variable local ' name '.|
|[ADVERTENCIA del compilador (nivel 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|código inaccesible|
|[ADVERTENCIA del compilador (nivel 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|posiblemente se ha utilizado una variable de puntero local '% s ' no inicializada|
|[ADVERTENCIA del compilador (nivel 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|asignación dentro de la expresión condicional|
|[ADVERTENCIA del compilador (nivel 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|operador de coma en la expresión de índice de matriz|
|[ADVERTENCIA del compilador (nivel 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'función': la función no está entre líneas|
|[ADVERTENCIA del compilador (nivel 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|función ' function ' seleccionada para expansión alineada automática|
|[ADVERTENCIA del compilador (nivel 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|función ' function ' marcada como __forceinline no insertada|
|[ADVERTENCIA del compilador (nivel 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|' función ': no todas las rutas de acceso de control devuelven un valor|
|[ADVERTENCIA del compilador (nivel 1, error) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|' función ': debe devolver un valor|
|[ADVERTENCIA del compilador (nivel 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|' función ': recursivo en todas las rutas de acceso de control. la función causará el desbordamiento de la pila en tiempo de ejecución|
|[ADVERTENCIA del compilador (nivel 4) C4718](compiler-warning-level-4-c4718.md)|' llamada a función ': la llamada recursiva no tiene efectos secundarios; se eliminará|
|ADVERTENCIA del compilador (nivel 1) C4719|Se encontró una constante Double cuando se especificó Qfast: Use ' f ' como sufijo para indicar una precisión sencilla|
|ADVERTENCIA del compilador (nivel 2) C4720|informes de ensamblador en línea: ' mensaje '|
|ADVERTENCIA del compilador (nivel 1) C4721|' función ': no está disponible como intrínseco|
|[ADVERTENCIA del compilador (nivel 1) C4722](compiler-warning-level-1-c4722.md)|' función ': el destructor nunca devuelve un, posible fuga de memoria|
|[ADVERTENCIA del compilador (nivel 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|División potencial por 0|
|[ADVERTENCIA del compilador (nivel 3) C4724](compiler-warning-level-3-c4724.md)|posible división (módulo) por 0|
|ADVERTENCIA del compilador (nivel 3) C4725|puede que la instrucción máquina sea incorrecta en algunos equipos Pentium|
|[ADVERTENCIA del compilador (nivel 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Se encontró un PCH llamado pch_file con la misma marca de tiempo en obj_file_1 y obj_file_2.  Utilizando el primer PCH.|
|ADVERTENCIA del compilador (nivel 1) C4728|Se omitió la opción/YL-porque se requiere la referencia PCH|
|ADVERTENCIA del compilador (nivel 4) C4729|función demasiado grande para advertencias basadas en gráficos de flujos|
|[Advertencia del compilador (nivel 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md) ADVERTENCIA del compilador (nivel 1) C4730|' Main ': la combinación de expresiones de _m64 y de punto flotante puede dar lugar a código incorrecto|
|[ADVERTENCIA del compilador (nivel 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|' Pointer ': el registro de puntero de marco ' Register ' modificado por el código de ensamblado alineado|
|ADVERTENCIA del compilador (nivel 1) C4732|la función '% s ' intrínseca no se admite en esta arquitectura|
|[ADVERTENCIA del compilador (nivel 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Asignación de ASM en línea a ' FS: 0 ': el controlador no está registrado como controlador seguro|
|[ADVERTENCIA del compilador (nivel 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento|
|[ADVERTENCIA del compilador (nivel 1) C4739](compiler-warning-level-1-c4739.md)|la referencia a la variable 'var' supera su espacio de almacenamiento|
|[ADVERTENCIA del compilador (nivel 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|fluir dentro o fuera del código ASM en línea suprime la optimización global|
|[ADVERTENCIA del compilador (nivel 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|' var ' tiene una alineación diferente en ' archivo1 ' y ' archivo2 ': número y número|
|[ADVERTENCIA del compilador (nivel 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|' type ' tiene un tamaño diferente en ' archivo1 ' y ' archivo2 ': número y número de bytes|
|[ADVERTENCIA del compilador (nivel 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|' var ' tiene un tipo diferente en ' archivo1 ' y ' archivo2 ': ' tipo1 ' y ' tipo2 '|
|[ADVERTENCIA del compilador C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|el acceso volátil de '*Expression*' está sujeto a la opción/volatile&#124;:\<ISO MS >. considere la posibilidad de usar __iso_volatile_load funciones intrínsecas/Store|
|[ADVERTENCIA del compilador (nivel 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Llamando a ' EntryPoint ' administrado: el código administrado no se puede ejecutar en un bloqueo del cargador, incluido el punto de entrada del archivo DLL y las llamadas alcanzadas desde el punto de entrada del archivo DLL|
|ADVERTENCIA del compilador (nivel 4) C4749|compatibilidad condicional: desplazamiento aplicado al tipo de diseño no estándar '*tipo*'|
|[ADVERTENCIA del compilador (nivel 1) C4750](compiler-warning-level-1-c4750.md)|'identificador': función con _alloca() insertada en un bucle|
|ADVERTENCIA del compilador (nivel 4) C4751|/Arch: AVX no se aplica a las extensiones SIMD de streaming de Intel (R) que se encuentran en ASM en línea|
|ADVERTENCIA del compilador (nivel 4) C4752|se encontraron extensiones de vector avanzadas de Intel (R). considere la posibilidad de usar/Arch: AVX|
|[ADVERTENCIA del compilador (nivel 4) C4754](compiler-warning-level-4-c4754.md)|Las reglas de conversión para las operaciones aritméticas en la comparación de% s (% d) significan que una bifurcación no se puede ejecutar. Convertir '% s ' en '% s ' (o un tipo similar de% d bytes).|
|ADVERTENCIA del compilador C4755|Las reglas de conversión para las operaciones aritméticas en la comparación de% s (% d) significan que una bifurcación no se puede ejecutar en una función insertada. Convertir '% s ' en '% s ' (o un tipo similar de% d bytes).|
|[ADVERTENCIA del compilador (nivel 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|desbordamiento en aritmética de constantes|
|ADVERTENCIA del compilador (nivel 4) C4757|el subíndice es un valor sin signo grande, ¿deseaba una constante negativa?|
|[ADVERTENCIA del compilador (nivel 4) C4764](compiler-warning-level-4-c4764.md)|No se pueden alinear objetos Catch a más de 16 bytes|
|ADVERTENCIA del compilador (nivel 4) C4767|el nombre de sección '% s ' tiene más de 8 caracteres y lo truncará el vinculador|
|ADVERTENCIA del compilador (nivel 3) C4768|se omiten los atributos de __declspec antes de la especificación de vinculación|
|ADVERTENCIA del compilador C4770|enumeración parcialmente validada '*Name*' utilizada como índice|
|ADVERTENCIA del compilador C4771|Los límites se deben crear con un puntero simple; Función de MPX intrínseca omitida|
|[ADVERTENCIA del compilador (nivel 1, error) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import hace referencia a un tipo de una biblioteca de tipos que falta; ' missing_type ' se usa como marcador de posición|
|ADVERTENCIA del compilador (nivel 4) C4774|'*cadena*': la cadena de formato esperada en el *número* de argumento no es un literal de cadena|
|ADVERTENCIA del compilador (nivel 3) C4775|extensión no estándar usada en la cadena de formato '*cadena*' de la función '*función*'|
|ADVERTENCIA del compilador (nivel 1) C4776|'%*character*' no se permite en la cadena de formato de la función '*function*'|
|ADVERTENCIA del compilador (nivel 4) C4777|'*función*': la cadena de formato '*cadena*' requiere un argumento de tipo '*tipo1*', pero el *número* de argumento de variádicas tiene el tipo '*tipo2*'|
|ADVERTENCIA del compilador (nivel 3) C4778|'*función*': cadena de formato no terminada '*cadena*'|
|[ADVERTENCIA del compilador (nivel 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|' Identifier ': el identificador se ha truncado a ' número ' caracteres|
|[ADVERTENCIA del compilador (nivel 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|se producirá una saturación del búfer 'identificador' con un tamaño de N bytes; se escribirán M bytes empezando en el desplazamiento L|
|ADVERTENCIA del compilador (nivel 2) C4792|función '% s ' declarada mediante sysimport y a la que se hace referencia desde código nativo; Biblioteca de importación necesaria para vincular|
|[ADVERTENCIA del compilador (niveles 1 y 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|' function ': función compilada como nativa: \ n\t ' Reason '|
|[ADVERTENCIA del compilador (nivel 1) C4794](compiler-warning-level-1-c4794.md)|el segmento de la variable de almacenamiento local de subprocesos '% s ' cambió de '% s ' a '% s '|
|[ADVERTENCIA del compilador (nivel 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|la función ' function ' no tiene ninguna instrucción EMMS|

## <a name="see-also"></a>Consulte también

[Errores yC++ advertencias de las herramientas de compilación y del compilador de C/](../compiler-errors-1/c-cpp-build-errors.md) \
[Advertencias del compilador C4000-C5999](compiler-warnings-c4000-c5999.md)
