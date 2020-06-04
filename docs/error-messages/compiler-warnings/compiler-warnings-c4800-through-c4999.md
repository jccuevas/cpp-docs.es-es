---
title: Advertencias del compilador de C4800 a C5999
ms.date: 04/21/2019
f1_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4916
- C4921
- C4934
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
helpviewer_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4916
- C4921
- C4934
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5106
- C5107
ms.openlocfilehash: 4d349ba8a51b324b5262e3e38506015ea198d5e3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438277"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Advertencias del compilador de C4800 a C5999

En los artículos de esta sección de la documentación se explica un subconjunto de los mensajes de advertencia generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Mensajes de advertencia

|Advertencia|Message|
|-------------|------------|
|[ADVERTENCIA del compilador (nivel 4) C4800](compiler-warning-level-3-c4800.md)| Conversión implícita de '*tipo*' a bool. Posible pérdida de información |
|[ADVERTENCIA del compilador (nivel 1) C4803](compiler-warning-level-1-c4803.md)|'*Method*': el método raise tiene una clase de almacenamiento diferente de la del evento, '*Event*'|
|[ADVERTENCIA del compilador (nivel 1) C4804](compiler-warning-level-1-c4804.md)|'*Operation*': uso no seguro del tipo ' bool ' en la operación|
|[ADVERTENCIA del compilador (nivel 1) C4805](compiler-warning-level-1-c4805.md)|'*Operation*': combinación no segura del tipo '*tipo1*' y tipo '*tipo2*' en la operación|
|[ADVERTENCIA del compilador (nivel 1) C4806](compiler-warning-level-1-c4806.md)|'*operación*': operación no segura: ningún valor de tipo '*tipo1*' promocionado al tipo '*tipo2*' puede ser igual a la constante especificada|
|[ADVERTENCIA del compilador (nivel 1) C4807](compiler-warning-level-1-c4807.md)|'*Operation*': combinación no segura del tipo '*tipo1*' y campo de bits con signo de tipo '*tipo2*'|
|ADVERTENCIA del compilador (nivel 1) C4808|Case '*Value*' no es un valor válido para la condición switch de tipo ' bool '|
|ADVERTENCIA del compilador (nivel 1) C4809|la instrucción switch tiene una etiqueta ' default ' redundante; se proporcionan todas las etiquetas posibles de ' Case '|
|[ADVERTENCIA del compilador (nivel 1) C4810](compiler-warning-level-1-c4810.md)|valor de pragma pack(show) == n|
|[ADVERTENCIA del compilador (nivel 1) C4811](compiler-warning-level-1-c4811.md)|valor de pragma conform(forScope, show) == %s|
|[ADVERTENCIA del compilador (nivel 1) C4812](compiler-warning-level-1-c4812.md)|estilo de declaración obsoleto: Use '*new_syntax*' en su lugar.|
|[ADVERTENCIA del compilador (nivel 1) C4813](compiler-warning-level-1-c4813.md)|'*función*': se debe haber declarado anteriormente una función Friend de una clase local|
|[ADVERTENCIA del compilador (nivel 4) C4816](compiler-warning-level-4-c4816.md)|'*param*': el parámetro tiene una matriz de tamaño cero que se truncará (a menos que el objeto se pase por referencia)|
|[ADVERTENCIA del compilador (nivel 1) C4817](compiler-warning-level-1-c4817.md)|'*member*': uso no válido de '. ' para obtener acceso a este miembro; el compilador se ha reemplazado por '-> '|
|[ADVERTENCIA del compilador (nivel 1) C4819](compiler-warning-level-1-c4819.md)|El archivo contiene un carácter que no se puede representar en la página de códigos actual (número). Guardar el archivo en formato Unicode para evitar la pérdida de datos|
|[ADVERTENCIA del compilador (nivel 4) C4820](compiler-warning-level-4-c4820.md)|'*bytes*' bytes de relleno agregados después de la construcción '*member_name*'|
|[ADVERTENCIA del compilador (nivel 1) C4821](compiler-warning-level-1-c4821.md)|No se puede determinar el tipo de codificación Unicode. Guarde el archivo con la firma (BOM).|
|[ADVERTENCIA del compilador (nivel 1) C4822](compiler-warning-level-1-c4822.md)|' función miembro ': la función miembro de clase local no tiene cuerpo|
|[ADVERTENCIA del compilador (nivel 3) C4823](compiler-warning-level-3-c4823.md)|'*función*': usa punteros anclados pero la semántica de desenredo no está habilitada. Considere la posibilidad de usar/EHa|
|ADVERTENCIA del compilador (nivel 2) C4826|La conversión de '*tipo1*' a '*tipo2*' tiene signo. Esto puede producir un comportamiento inesperado en tiempo de ejecución.|
|ADVERTENCIA del compilador (nivel 3) C4827|Un método ' ToString ' público con 0 parámetros debe marcarse como virtual e invalidar|
|[ADVERTENCIA del compilador (nivel 1) C4829](compiler-warning-level-1-c4829.md)|Parámetros posiblemente incorrectos para la función main. Considere ' int Main (Platform:: Array\<Platform:: String ^ > ^ argv) '|
|[ADVERTENCIA del compilador (nivel 1) C4835](compiler-warning-level-1-c4835.md)|'*variable*': el inicializador de los datos exportados no se ejecutará hasta que el código administrado se ejecute por primera vez en el ensamblado de host|
|ADVERTENCIA del compilador (nivel 4) C4837|se detectó un trígrafo: '?? *carácter*' reemplazado por '*carácter*'|
|[ADVERTENCIA del compilador (nivel 1) C4838](compiler-warning-level-1-c4838.md)|la conversión de '*TYPE_1*' a '*TYPE_2*' requiere una conversión de restricción|
|[ADVERTENCIA del compilador (nivel 3) C4839](compiler-warning-level-3-c4839.md)|uso no estándar de la clase '*Type*' como argumento de una función variádicas|
|[ADVERTENCIA del compilador (nivel 4) C4840](compiler-warning-level-4-c4840.md)|uso no portátil de la clase '*Type*' como argumento de una función variádicas|
|ADVERTENCIA del compilador (nivel 4) C4841|se ha utilizado una extensión no estándar: designador de miembro compuesto usado en DESREF|
|ADVERTENCIA del compilador (nivel 4) C4842|no se garantiza que el resultado de ' offsetto ' aplicado a un tipo mediante herencia múltiple sea coherente entre versiones del compilador|
|ADVERTENCIA del compilador C4843|'*tipo1*': no se puede tener acceso a un controlador de excepciones de referencia a un tipo de función o matriz, use '*Type2*' en su lugar|
|ADVERTENCIA del compilador C4844|' Export Module *MODULE_NAME*; ' es ahora la sintaxis preferida para declarar una interfaz de módulo|
| ADVERTENCIA del compilador (nivel 4) C4845 | se omite '\_\_declspec (no\_init\_All) ' si '/d1initall\[0\|1\|2\|3] ' no se especificó en la línea de comandos |
| ADVERTENCIA del compilador (nivel 4) C4846 | '*valor*' no es un argumento válido para '/d1initall ': se omitió la marca de la línea de comandos |
| ADVERTENCIA del compilador (nivel 4) C4847 | '\_\_declspec (no\_init\_All) ' solo se puede aplicar a una función, un tipo de clase o una variable local: se omite |
| ADVERTENCIA del compilador (nivel 1) C4848 | la compatibilidad con el atributo estándar ' no\_dirección\_única ' en C++ 17 y versiones anteriores es una extensión de proveedor |
|[ADVERTENCIA del compilador (nivel 4) C4866](c4866.md)| el compilador no puede aplicar el orden de evaluación de izquierda a derecha para llamar a *operator_name*|
|[ADVERTENCIA del compilador (error) C4867](compiler-warning-c4867.md)|'*función*': falta la lista de argumentos de la llamada de función; usar '*Call*' para crear un puntero a un miembro|
|[ADVERTENCIA del compilador (nivel 4) C4868](compiler-warning-c4868.md)|el compilador '_File_(*line_number*) ' no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicialización entre llaves|
|ADVERTENCIA del compilador (nivel 2) C4872|División de punto flotante por cero detectada al compilar el gráfico de llamadas para Concurrency::p arallel_for_each en: '*Location*'|
|ADVERTENCIA del compilador (nivel 1) C4880|conversión de ' const *TYPE_1*' a '*TYPE_2*': la conversión de const desde un puntero o una referencia puede dar lugar a un comportamiento indefinido en una función con restricción de amp|
|ADVERTENCIA del compilador (nivel 4) C4881|no se invocará al constructor ni al destructor para tile_static variable '*variable*'|
|ADVERTENCIA del compilador (nivel 1) C4882|pasar los funcdores con operadores de llamada no const a Concurrency::p arallel_for_each está en desuso|
|[ADVERTENCIA del compilador C4900](compiler-warning-level-1-c4900.md)|Error de coincidencia de Il entre '*Tool1*' versión '*version1*' y '*Tool2*' versión '*version2*'|
|[ADVERTENCIA del compilador (nivel 1) C4905](compiler-warning-level-1-c4905.md)|conversión de literal de cadena de tipo ancho a 'LPSTR'|
|[ADVERTENCIA del compilador (nivel 1) C4906](compiler-warning-level-1-c4906.md)|conversión de literal de cadena a 'LPWSTR'|
|[ADVERTENCIA del compilador (nivel 1) C4910](compiler-warning-level-1-c4910.md)|'\<identificador >: ' __declspec (dllexport) ' y ' extern ' son incompatibles en una creación de instancias explícita|
|[ADVERTENCIA del compilador (nivel 1) C4912](compiler-warning-level-1-c4912.md)|'*Attribute*': el atributo tiene un comportamiento indefinido en un UDT anidado|
|[ADVERTENCIA del compilador (nivel 4) C4913](compiler-warning-level-4-c4913.md)|el operador binario ',' definido por el usuario existe pero ninguna sobrecarga puede convertir todos los operandos; en su lugar, se utilizará el operador binario ',' incorporado|
|ADVERTENCIA del compilador (nivel 1) C4916|para tener un DISPID, '*Description*': se debe introducir mediante una interfaz|
|[ADVERTENCIA del compilador (nivel 1) C4917](compiler-warning-level-1-c4917.md)|'*declarador*': un GUID solo se puede asociar a una clase, interfaz o espacio de nombres|
|[ADVERTENCIA del compilador (nivel 4) C4918](compiler-warning-level-4-c4918.md)|'*carácter*': carácter no válido en la lista de optimización de pragma|
|[ADVERTENCIA del compilador (nivel 1) C4920](compiler-warning-level-1-c4920.md)|Enum Enum Member member_1 = value_1 ya se ha detectado en Enum Enum as member_2 = value_2|
|ADVERTENCIA del compilador (nivel 3) C4921|'*Description*': el valor de atributo '*Attribute*' no se debe multiplicar|
|[ADVERTENCIA del compilador (nivel 1) C4925](compiler-warning-level-1-c4925.md)|'*Method*': no se puede llamar al método dispinterface desde el script|
|[ADVERTENCIA del compilador (nivel 1) C4926](compiler-warning-level-1-c4926.md)|'*Identifier*': ya se ha definido el símbolo: se han omitido los atributos|
|[ADVERTENCIA del compilador (nivel 1) C4927](compiler-warning-level-1-c4927.md)|conversión no válida; se aplicó implícitamente más de una conversión definida por el usuario|
|[ADVERTENCIA del compilador (nivel 1) C4928](compiler-warning-level-1-c4928.md)|inicialización de copia no válida; se aplicó implícitamente más de una conversión definida por el usuario|
|[ADVERTENCIA del compilador (nivel 1) C4929](compiler-warning-level-1-c4929.md)|'*File*': biblioteca contiene una Unión; omitiendo el calificador ' embedded_idl '|
|[ADVERTENCIA del compilador (nivel 1) C4930](compiler-warning-level-1-c4930.md)|'*prototype*': no se ha llamado a la función prototipo (¿se ha diseñado una definición de variable?)|
|[ADVERTENCIA del compilador (nivel 4) C4931](compiler-warning-level-4-c4931.md)|se supone que la biblioteca de tipos se compiló para punteros de (número) bits|
|[ADVERTENCIA del compilador (nivel 4) C4932](compiler-warning-level-4-c4932.md)|__identifier (*Identifier*) y \__identifier (*Identifier*) no se pueden distinguir|
|ADVERTENCIA del compilador (nivel 1) C4934|' __delegate (multidifusión) ' está en desuso. en su lugar, use '\__delegate '.|
|[ADVERTENCIA del compilador (nivel 1) C4935](compiler-warning-level-1-c4935.md)|especificador de acceso de ensamblado modificado desde '*Access*'|
|[ADVERTENCIA del compilador (nivel 1, error) ADVERTENCIA c4936](compiler-warning-c4936.md)|__declspec se admite solamente cuando se compila con /clr o /clr:pure|
|[ADVERTENCIA del compilador (nivel 4) C4937](compiler-warning-level-4-c4937.md)|'*texto1*' y '*texto2*' no se pueden distinguir como argumentos para '*Directiva*'|
|[ADVERTENCIA del compilador (nivel 4) C4938](compiler-warning-level-4-c4938.md)|'*var*': la variable de reducción de punto flotante puede producir resultados incoherentes bajo/FP: strict o #pragma fenv_access|
|[ADVERTENCIA del compilador C4939](compiler-warning-level-1-c4939.md)|#pragma vtordisp está en desuso y se quitará en una próxima versión de Visual C++|
|[ADVERTENCIA del compilador (nivel 1) C4944](compiler-warning-level-1-c4944.md)|'*Symbol*': no se puede importar el símbolo desde '*Assembly1*': ya que '*Symbol*' ya existe en el ámbito actual|
|[ADVERTENCIA del compilador (nivel 1) C4945](compiler-warning-level-1-c4945.md)|'*Symbol*': no se puede importar el símbolo desde '*Assembly1*': ya se ha importado '*Symbol*' desde otro ensamblado '*assembly2*'|
|[ADVERTENCIA del compilador (nivel 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast usar entre las clases relacionadas: '*Class1*' y '*clase2*'|
|[ADVERTENCIA del compilador (nivel 1) C4947](compiler-warning-level-1-c4947.md)|'*type_or_member*': marcado como obsoleto|
|[ADVERTENCIA del compilador (nivel 2) C4948](compiler-warning-level-2-c4948.md)|el tipo de valor devuelto de '*accessor*' no coincide con el último tipo de parámetro del establecedor correspondiente|
|[ADVERTENCIA del compilador (nivel 1 y nivel 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|las pragmas ' Managed ' y ' Unmanaged ' solo son significativas cuando se compilan con '/CLR [: opción] '|
|[ADVERTENCIA del compilador (nivel 1, error) C4950](compiler-warning-c4950.md)|'*type_or_member*': marcado como obsoleto|
|[ADVERTENCIA del compilador (nivel 1) C4951](compiler-warning-level-1-c4951.md)|'*function*' se ha editado desde que se recopilaron los datos de perfil; los datos de Perfil de función no se usan|
|[ADVERTENCIA del compilador (nivel 1) C4952](compiler-warning-level-1-c4952.md)|'*función*': no se encontraron datos de perfil en la base de datos de programa '*pgd_file*'|
|[ADVERTENCIA del compilador (nivel 1) C4953](compiler-warning-level-1-c4953.md)|La '*función*' insertada se ha editado desde que se recopilaron los datos de perfil; los datos de perfil no se usan|
|ADVERTENCIA del compilador C4954|'*función*': sin perfiles (contiene __int64 expresión switch)|
|ADVERTENCIA del compilador C4955|'*import2*': importación omitida; ya se importó desde '*import1*'|
|[ADVERTENCIA del compilador (nivel 1, error) C4956](compiler-warning-c4956.md)|'*Type*': este tipo no se pudo comprobar|
|[ADVERTENCIA del compilador (nivel 1, error) C4957](compiler-warning-c4957.md)|'*Cast*': la conversión explícita de '*cast_from*' a '*cast_to*' no es comprobable|
|[ADVERTENCIA del compilador (nivel 1, error) C4958](compiler-warning-c4958.md)|'*Operation*': la aritmética de puntero no se pudo comprobar|
|[ADVERTENCIA del compilador (nivel 1, error) C4959](compiler-warning-c4959.md)|no se puede definir el tipo no administrado '*Type*' en/clr: safe porque el acceso a sus miembros produce código no comprobable|
|[ADVERTENCIA del compilador (nivel 4) C4960](compiler-warning-level-4-c4960.md)|'*function*' es demasiado grande para el que se va a crear el archivo|
|[ADVERTENCIA del compilador (nivel 1) C4961](compiler-warning-c4961.md)|No se combinó ningún dato de perfil en 'archivo .pgd'; se han deshabilitado las optimizaciones guiadas por perfil.|
|[ADVERTENCIA del compilador (nivel 4) C4962](compiler-warning-c4962.md)|'*función*': se han deshabilitado las optimizaciones guiadas por perfiles porque las optimizaciones produjeron datos de perfil incoherentes|
|ADVERTENCIA del compilador (nivel 1) C4963|'*Description*': no se encontraron datos de perfil; se usaron diferentes opciones del compilador en la compilación instrumentada|
|[ADVERTENCIA del compilador (nivel 1) C4964](compiler-warning-level-1-c4964.md)|No se especificaron opciones de optimización; no se recopilará la información de perfil|
|[ADVERTENCIA del compilador (nivel 1) C4965](compiler-warning-level-1-c4965.md)|cuadro implícito de entero 0; usar nullptr o conversión explícita|
|ADVERTENCIA del compilador (nivel 1) C4966|'*function*' tiene __code_seg anotación con un nombre de segmento no admitido; se omitió la anotación|
|ADVERTENCIA del compilador C4970|constructor delegado: el objeto de destino se omitió porque '*Type*' es estático|
|ADVERTENCIA del compilador (nivel 1) C4971|Orden de los argumentos: \<objeto de destino >, \<> de la función de destino para el constructor delegado está en desuso, use \<función de destino >, \<objeto de destino = "" >|
|[ADVERTENCIA del compilador (nivel 1, error) C4972](compiler-warning-c4972.md)|No se puede comprobar la modificación o el tratamiento directo del resultado de una operación de conversión unbox como valor L|
|ADVERTENCIA del compilador (nivel 1) C4973|'*Symbol*': marcado como desusado|
|ADVERTENCIA del compilador (nivel 1) C4974|'*Symbol*': marcado como desusado|
|ADVERTENCIA del compilador (nivel 3) C4981|Warbird: la función '*function*' marcada como __forceinline no está insertada porque contiene semántica de excepción|
|[ADVERTENCIA del compilador C4984](compiler-warning-c4984.md)|' if constexpr ' es una extensión del lenguaje C++ 17|
|[ADVERTENCIA del compilador (nivel 4) C4985](compiler-warning-level-4-c4985.md)|'*symbol_name*': atributos no presentes en la declaración anterior.|
|[ADVERTENCIA del compilador C4986](compiler-warning-c4986.md)|'*declaration*': la especificación de la excepción no coincide con la declaración anterior|
|ADVERTENCIA del compilador (nivel 4) C4987|se usó una extensión no estándar: 'throw (...)'|
|ADVERTENCIA del compilador (nivel 4) C4988|'*variable*': variable declarada fuera del ámbito de clase o función|
|ADVERTENCIA del compilador (nivel 4) C4989|'*tipo*': el tipo tiene definiciones en conflicto.|
|ADVERTENCIA del compilador (nivel 3) C4990|Warbird: *mensaje*|
|ADVERTENCIA del compilador (nivel 3) C4991|Warbird: la función '*function*' marcada como __forceinline no está insertada porque el nivel de protección de inline es mayor que el elemento primario|
|ADVERTENCIA del compilador (nivel 3) C4992|Warbird: la función '*function*' marcada como __forceinline no está insertada porque contiene un ensamblado alineado que no se puede proteger|
|[ADVERTENCIA del compilador (nivel 3) C4995](compiler-warning-level-3-c4995.md)|'*función*': el nombre se marcó como #pragma en desuso|
|[ADVERTENCIA del compilador (nivel 3) C4996](compiler-warning-level-3-c4996.md)|'*deprecated-declaration*': *el mensaje de desuso* (o "se declaró en desuso")|
|[ADVERTENCIA del compilador (nivel 1) C4997](compiler-warning-level-1-c4997.md)|'*Class*': la coclase no implementa una interfaz com ni una pseudo-interfaz|
|ADVERTENCIA del compilador (nivel 1) C4998|ERROR de EXPECTAtiva: *expectativa*(*valor*)|
|[ADVERTENCIA del compilador C4999](compiler-warning-level-1-c4999.md)|ADVERTENCIA desconocida elija el comando soporte técnico en el menú Ayuda C++ visual o abra el archivo de ayuda de soporte técnico para obtener más información.|
|ADVERTENCIA del compilador C5022|'*Type*': se especificaron varios constructores de movimiento|
|ADVERTENCIA del compilador C5023|'*Type*': se especificaron varios operadores de asignación de movimiento|
|ADVERTENCIA del compilador (nivel 4) C5024|'*Type*': el constructor de movimiento se definió implícitamente como eliminado|
|ADVERTENCIA del compilador (nivel 4) C5025|'*Type*': el operador de asignación de movimiento se definió implícitamente como eliminado|
|ADVERTENCIA del compilador (nivel 1 y nivel 4) C5026|'*Type*': el constructor de movimiento se definió implícitamente como eliminado|
|ADVERTENCIA del compilador (nivel 1 y nivel 4) C5027|'*Type*': el operador de asignación de movimiento se definió implícitamente como eliminado|
|ADVERTENCIA del compilador (nivel 1) C5028|'*Name*': la alineación especificada en la declaración anterior (*número*) no se ha especificado en la definición|
|ADVERTENCIA del compilador (nivel 4) C5029|se ha utilizado una extensión no estándar: C++ los atributos de alineación de solo se aplican a variables, miembros de datos y tipos de etiqueta|
|ADVERTENCIA del compilador (nivel 3) C5030|no se reconoce el atributo '*atributo*'|
|ADVERTENCIA del compilador (nivel 4) C5031|ADVERTENCIA de #pragma (pop): probable falta de coincidencia, se insertó el estado de advertencia insertado en un archivo diferente|
|ADVERTENCIA del compilador (nivel 4) C5032|se detectó #pragma ADVERTENCIA (inserciones) sin #pragma ADVERTENCIA (pop) correspondiente|
|ADVERTENCIA del compilador (nivel 1) C5033|'*Storage-Class*' ya no es una clase de almacenamiento admitida|
|ADVERTENCIA del compilador C5034|el uso de '*Intrinsic*' intrínseco hace que la *función* de función se compile como código de invitado|
|ADVERTENCIA del compilador C5035|el uso de la característica '*Feature*' hace que la *función* de función se compile como código de invitado|
|ADVERTENCIA del compilador (nivel 1) C5036|conversión del puntero de función varargs al compilar con/Hybrid: x86arm64 '*tipo1*' en '*Type2*'|
|ADVERTENCIA del compilador (error) C5037|'*miembro-función*': una definición fuera de línea de un miembro de una plantilla de clase no puede tener argumentos predeterminados|
|[ADVERTENCIA del compilador (nivel 4) C5038](c5038.md)|el miembro de datos '*member1*' se inicializará después del miembro de datos '*miembro2*'|
|ADVERTENCIA del compilador (nivel 4) C5039|'*function*': puntero o referencia a una función de inicio que se pasa a la función extern C en-EHC. Se puede producir un comportamiento indefinido si esta función produce una excepción.|
|ADVERTENCIA del compilador (nivel 3) C5040|las especificaciones de excepciones dinámicas solo son válidas en C++ 14 y versiones anteriores; tratar como noexception (false)|
|ADVERTENCIA del compilador (nivel 1) C5041|'*Definition*': la definición fuera de línea para el miembro de datos estático constexpr no es necesaria y está en desuso en c++ 17|
|ADVERTENCIA del compilador (nivel 3) C5042|'*declaration*': las declaraciones de función en el ámbito de bloque no se pueden especificar como ' C++inline ' en el estándar; quitar el especificador "inline"|
|ADVERTENCIA del compilador (nivel 2) los errores c5043|'*Specification*': la especificación de la excepción no coincide con la declaración anterior|
|ADVERTENCIA del compilador (nivel 4) C5044|Un argumento de la opción de la línea de *comandos apunta a* una ruta de acceso '*path*' que no existe|
| [ADVERTENCIA del compilador C5045](c5045.md) | El compilador insertará la mitigación de Spectre para la carga de memoria si se especifica el modificador/Qspectre |
| [ADVERTENCIA del compilador (nivel 2) C5046](c5046.md) | '*función*': símbolo que implica el tipo con vinculación interna no definida |
| ADVERTENCIA del compilador (nivel 1) C5047 | no se admite el uso de \_no estándar \_si\_existe con los módulos |
| ADVERTENCIA del compilador (nivel 1) C5048 | El uso de la macro '*nombremacro*' puede dar lugar a resultados no deterministas |
| ADVERTENCIA del compilador (nivel 1) C5049 | '*cadena*': la incrustación de una ruta de acceso completa puede tener como resultado una salida dependiente del equipo |
| ADVERTENCIA del compilador (nivel 1) C5050 | Posible entorno incompatible al importar el módulo '*MODULE_NAME*': *problema* |
| ADVERTENCIA del compilador (nivel 1) C5100 | \_\_VA\_ARGS\_\_ está reservado para su uso en macros variádicas |
| ADVERTENCIA del compilador (nivel 1) C5101 | el uso de la Directiva de preprocesador en la lista de argumentos de macro de tipo función es un comportamiento indefinido |
| ADVERTENCIA del compilador (nivel 1) C5102 | se omitirá la definición de macro de línea de comandos no válida '*Value*' |
| ADVERTENCIA del compilador (nivel 1) C5103 | pegar '*token1*' y '*token2*' no produce un token de preprocesamiento válido |
| ADVERTENCIA del compilador (nivel 1) C5104 | se encontró '*cadena1*#*cadena2*' en la lista de reemplazo de macros, ¿quiso decir '*cadena1*' "#*cadena2*'? |
| [ADVERTENCIA del compilador (nivel 1) C5105](c5105.md) | la expansión de macros que produce ' defined ' tiene un comportamiento indefinido |
| ADVERTENCIA del compilador (nivel 1) C5106 | macro redefinida con distintos nombres de parámetro |
| ADVERTENCIA del compilador (nivel 1) C5107 | falta el carácter '*carácter*' de terminación |

## <a name="see-also"></a>Consulte también

[Errores yC++ advertencias de las herramientas de compilación y del compilador de C/](../compiler-errors-1/c-cpp-build-errors.md) \
[Advertencias del compilador C4000-C5999](compiler-warnings-c4000-c5999.md)
