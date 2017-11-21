---
title: "C4800 de advertencias del compilador a través de C5999 | Documentos de Microsoft"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords:
- C4806
- C4807
- C4808
- C4809
- C4810
- C4811
- C4812
- C4813
- C4816
- C4817
- C4822
- C4825
- C4827
- C4837
- C4840
- C4841
- C4842
- C4872
- C4880
- C4881
- C4882
- C4900
- C4910
- C4912
- C4913
- C4916
- C4918
- C4920
- C4921
- C4925
- C4926
- C4932
- C4934
- C4935
- C4936
- C4937
- C4938
- C4939
- C4944
- C4947
- C4950
- C4951
- C4952
- C4953
- C4954
- C4955
- C4956
- C4957
- C4958
- C4959
- C4960
- C4961
- C4962
- C4963
- C4966
- C4970
- C4971
- C4972
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4997
- C4998
- C4999
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
- C5038
dev_langs: C++
ms.assetid: c3182430-8b3b-4ab2-a532-5cd436707dc8
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bf919fbb1959af6fad031a7f32262466f6f49ff
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warnings-c4800-through-c5999"></a>C4800 de advertencias del compilador a través de C5999

Los artículos de esta parte de la documentación contienen información sobre un subconjunto de las advertencias del compilador de Visual C++. Puede tener acceso a información aquí o bien, en la ventana de salida en Visual Studio, puede seleccionar un número de error y, a continuación, presione la tecla F1.

> [!NOTE]
> No todos [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] error o advertencia está documentado en MSDN. En muchos casos, el mensaje de diagnóstico proporciona toda la información que está disponible. Si cree que un mensaje de error necesita una explicación adicional, puede enviarnos su opinión. Puede utilizar el formulario de comentarios de esta página, o vaya a la barra de menús de Visual Studio y elija **ayuda**, **notificar un error**, o puede enviar un informe de sugerencia o un error en [Microsoft Connect](http://connect.microsoft.com/VisualStudio).

Puede encontrar ayuda adicional sobre errores y advertencias en los foros públicos de MSDN. El [lenguaje Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) es foro para preguntas y debate sobre el [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] sintaxis del lenguaje y compilador. El [General de Visual C++](http://go.microsoft.com/fwlink/?LinkId=158194) es foro para preguntas sobre [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] que no se debaten en otros foros. También puede encontrar ayuda sobre los errores y advertencias en [desbordamiento de la pila](http://stackoverflow.com/).

## <a name="in-this-section"></a>En esta sección

|Advertencia|Mensaje|
|-------------|-------------|
|[Advertencia del compilador (nivel 3) C4800](compiler-warning-level-3-c4800.md)|'type': forzando el valor a bool 'true' o 'false' (advertencia de rendimiento)|
|[Advertencia del compilador (nivel 1) C4803](compiler-warning-level-1-c4803.md)|'método': el método raise tiene una clase de almacenamiento distinta de la del evento, 'event'|
|[Advertencia del compilador (nivel 1) C4804](compiler-warning-level-1-c4804.md)|'operación': uso no seguro del tipo 'bool' en la operación|
|[Advertencia del compilador (nivel 1) C4805](compiler-warning-level-1-c4805.md)|'operación': combinación no segura del tipo 'type' y tipo 'tipo' en la operación|
|Advertencia del compilador (nivel 1) C4806|'operación': operación no segura: ningún valor de tipo 'tipo' promovido al tipo 'tipo' puede igualar la constante proporcionada|
|Advertencia del compilador (nivel 1) C4807|'operación': combinación no segura del tipo 'type' y el campo de bits con signo de tipo 'type'|
|Advertencia del compilador (nivel 1) C4808|Case 'valor' no es un valor válido para la condición switch de tipo 'booleano'|
|Advertencia del compilador (nivel 1) C4809|instrucción switch tiene una etiqueta 'default' redundante; se proporcionan todas las etiquetas 'case' posibles|
|Advertencia del compilador (nivel 1) C4810|valor de pragma pack(show) == n|
|Advertencia del compilador (nivel 1) C4811|valor de pragma conform(forScope, show) == %s|
|Advertencia del compilador (nivel 1) C4812|estilo de declaración obsoleto: use 'new_syntax' en su lugar|
|Advertencia del compilador (nivel 1) C4813|'función': debe haber declarado anteriormente una función friend de una clase local|
|Advertencia del compilador (nivel 4) C4816|'param': el parámetro tiene una matriz de tamaño cero que se truncará (a menos que el objeto se pasa por referencia)|
|Advertencia del compilador (nivel 1) Advertencia C4817|'miembro': uso no válido de '.' para obtener acceso a este miembro; compilador lo reemplazó por '->'|
|[Advertencia del compilador (nivel 1) C4819](compiler-warning-level-1-c4819.md)|El archivo contiene un carácter que no se puede representar en la página de códigos actual (número). Guarde el archivo en formato Unicode para evitar la pérdida de datos|
|[Advertencia del compilador (nivel 4) C4820](compiler-warning-level-4-c4820.md)|'bytes' bytes de relleno agregados después de construcción 'nombre_miembro'|
|[Advertencia del compilador (nivel 1) C4821](compiler-warning-level-1-c4821.md)|No se puede determinar el tipo de codificación Unicode, guarde el archivo con firma (l. MAT)|
|Advertencia del compilador (nivel 1) C4822|'member function': función miembro de clase local no tiene un cuerpo|
|[Advertencia del compilador (nivel 3) C4823](compiler-warning-level-3-c4823.md)|'función': utiliza punteros anclados de desenredo pero una semántica no está habilitada. Considere el uso de /EHa|
|Advertencia del compilador (nivel 2) C4826|Conversión de '*type1*'to'*type2*' es la extensión de signo. Esto puede provocar un comportamiento inesperado en tiempo de ejecución.|
|Advertencia del compilador (nivel 3) C4827|Un método público de 'ToString' con 0 parámetros debe marcarse como virtual y reemplazar|
|[Advertencia del compilador (nivel 1) C4829](compiler-warning-level-1-c4829.md)|Parámetros posiblemente incorrectos para la función main. Considere ' int main (Platform:: Array\<Platform:: String ^ > ^ argv)'|
|[Advertencia del compilador (nivel 1) C4835](compiler-warning-level-1-c4835.md)|'variable': el inicializador para los datos exportados no se ejecutará hasta que el código administrado se ejecuta primero en el ensamblado de host|
|Advertencia del compilador (nivel 4) C4837|se detectó un trígrafo: '?? *caracteres*'reemplazado por'*caracteres*'|
|[Advertencia del compilador (nivel 1) C4838](compiler-warning-level-1-c4838.md)|la conversión de 'type_1' a 'type_2' requiere una conversión de restricción|
|[Advertencia del compilador (nivel 3) C4839](compiler-warning-level-3-c4839.md)|uso no estándar de la clase*tipo*' como argumento a una función variádica|
|Advertencia del compilador (nivel 4) C4840|uso de no portable de la clase*tipo*' como argumento a una función variádica|
|Advertencia del compilador (nivel 4) C4841|ha utilizado una extensión no estándar: designador de miembro compuesta utilizado en offsetof|
|Advertencia del compilador (nivel 4) C4842|el resultado de 'offsetof' aplicado a un tipo mediante herencia múltiple no se garantiza que sea coherente entre las versiones del compilador|
|[(Error) de advertencia del compilador C4867](compiler-warning-c4867.md)|'función': falta la lista de argumentos; la llamada a función Use 'llamar a' para crear un puntero a miembro|
|[Compilador advertencia (nivel 4) C4868](compiler-warning-c4868.md)|'_archivo_(*line_number*)' compilador no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicialización entre llaves|
|Advertencia del compilador (nivel 2) C4872|división de punto flotante por cero detectado al compilar el gráfico de llamadas para Concurrency:: parallel_for_each en: '*ubicación*'|
|Advertencia del compilador (nivel 1) C4880|realiza la conversión de 'const type_1' a 'type_2': conversión fuera constness desde un puntero o referencia puede provocar un comportamiento indefinido en una función de amp restringido|
|Advertencia del compilador (nivel 4) C4881|el constructor o destructor no se invocará para tile_static variable 'variable'|
|Advertencia del compilador (nivel 1) C4882|pasar objetos functor con operadores de llamada no es const a Concurrency:: parallel_for_each está en desuso|
|C4900 de advertencia del compilador|Error de coincidencia de lenguaje intermedio entre 'tool1' versión 'version1' y 'tool2' versión 'version2'|
|[Advertencia del compilador (nivel 1) C4905](compiler-warning-level-1-c4905.md)|conversión de literal de cadena de tipo ancho a 'LPSTR'|
|[Advertencia del compilador (nivel 1) C4906](compiler-warning-level-1-c4906.md)|conversión de literal de cadena a 'LPWSTR'|
|Advertencia del compilador (nivel 1) C4910|'\<identificador >: '__declspec (dllexport)' y 'extern' son incompatibles en una instancia explícita|
|Advertencia del compilador (nivel 1) C4912|'attribute': el atributo tiene un comportamiento indefinido en un tipo definido por el usuario anidado|
|Advertencia del compilador (nivel 4) Advertencia C4913|el operador binario ',' definido por el usuario existe pero ninguna sobrecarga puede convertir todos los operandos; en su lugar, se utilizará el operador binario ',' incorporado|
|Advertencia del compilador (nivel 1) C4916|para tener un dispid, '*descripción*': debe producirse debido a una interfaz|
|[Advertencia del compilador (nivel 1) C4917](compiler-warning-level-1-c4917.md)|'declarador': un GUID solo puede asociarse con una clase, interfaz o espacio de nombres|
|Advertencia del compilador (nivel 4) C4918|'carácter': carácter no válido en la lista de optimizaciones de pragma|
|Advertencia del compilador (nivel 1) C4920|enum enum miembro member_1 = value_1 ya se vió en enum enum como member_2 = value_2|
|Advertencia del compilador (nivel 3) C4921|'*descripción*': valor del atributo '*atributo*' no debe especificarse varias veces|
|Advertencia del compilador (nivel 1) C4925|'method': no se puede llamar al método dispinterface desde el script|
|Advertencia del compilador (nivel 1) C4926|'identificador': ya se ha definido el símbolo: se han omitido los atributos.|
|[Advertencia del compilador (nivel 1) C4927](compiler-warning-level-1-c4927.md)|conversión no válida; se aplicó implícitamente más de una conversión definida por el usuario|
|[Advertencia del compilador (nivel 1) C4928](compiler-warning-level-1-c4928.md)|inicialización de copia no válida; se aplicó implícitamente más de una conversión definida por el usuario|
|[Advertencia del compilador (nivel 1) C4929](compiler-warning-level-1-c4929.md)|'archivo': biblioteca de tipos contiene una unión; se omitirá el calificador 'embedded_idl'|
|[Advertencia del compilador (nivel 1) C4930](compiler-warning-level-1-c4930.md)|'prototipo': no se llama a la función prototipo (era pensada una definición de variable?)|
|[Advertencia del compilador (nivel 4) C4931](compiler-warning-level-4-c4931.md)|se supone que la biblioteca de tipos se compiló para punteros de (número) bits|
|Advertencia del compilador (nivel 4) C4932|__identifier (*identificador*) y \__identifier (*identificador*) no es posible distinguir|
|Advertencia del compilador (nivel 1) C4934|'__delegate' está en desuso, use '\__delegate' en su lugar|
|Advertencia del compilador (nivel 1) C4935|especificador de acceso de ensamblado modificado desde 'access'|
|Advertencia del compilador (nivel 1, Error) Advertencia C4936|__declspec se admite solamente cuando se compila con /clr o /clr:pure|
|Advertencia del compilador (nivel 4) C4937|'texto1' y 'texto2' no se pueden distinguir como argumentos para 'directiva'|
|Advertencia del compilador (nivel 4) C4938|'var': variable de reducción de punto flotante puede causar resultados incoherentes bajo/fp: strict o #pragma fenv_access|
|Advertencia C4939 del compilador|#pragma vtordisp está en desuso y se quitará en una próxima versión de Visual C++|
|Advertencia del compilador (nivel 1) C4944|'símbolo': no se puede importar un símbolo desde 'assembly1': 'símbolo' ya existe en el ámbito actual|
|[Advertencia del compilador (nivel 1) C4945](compiler-warning-level-1-c4945.md)|'símbolo': no se puede importar un símbolo desde 'assembly1': como 'símbolo' ya se ha importado desde otro ensamblado 'assembly2'|
|[Advertencia del compilador (nivel 1) C4946](compiler-warning-level-1-c4946.md)|se utilizó reinterpret_cast entre clases relacionadas: 'clase1' y 'clase2'|
|Advertencia del compilador (nivel 1) C4947|'tipo_o_miembro': marcado como obsoleto|
|[Advertencia del compilador (nivel 2) C4948](compiler-warning-level-2-c4948.md)|tipo de valor devuelto de 'accessor' no coincide con el tipo último parámetro del método establecedor correspondiente|
|[Advertencia del compilador (niveles 1 y 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|pragma (directivas) 'administrado' y 'unmanaged' es significativos cuando se compila con ' / clr [: opción]'|
|Advertencia del compilador (nivel 1, Error) C4950|'tipo_o_miembro': marcado como obsoleto|
|Advertencia del compilador (nivel 1) C4951|'function' se ha editado desde que se recopilaron los datos de perfil; los datos de perfil de la función no se han utilizado|
|Advertencia del compilador (nivel 1) C4952|'función': se encontró ningún dato de perfil en la base de datos de programa 'archivo_pgd'|
|Advertencia del compilador (nivel 1) C4953|La inclusión en líneas de 'function' se ha editado desde que los datos de perfil se recopilaron; datos de perfil no utilizados|
|C4954 de advertencia del compilador|'función': no perfilado (contiene la expresión switch __int64)|
|C4955 de advertencia del compilador|'import2': importación omitida; ya se importó desde 'import1'|
|Advertencia del compilador (nivel 1, Error) Advertencia C4956|'type': este tipo no es comprobable|
|Advertencia del compilador (nivel 1, Error) Advertencia C4957|'conversión': conversión explícita de 'cast de' a 'cast_to' no es comprobable|
|Advertencia del compilador (nivel 1, Error) Advertencia C4958|'operación': la aritmética con punteros no es comprobable|
|Advertencia del compilador (nivel 1, Error) Advertencia C4959|no se puede definir un tipo no administrado 'type' en/CLR: safe porque el acceso a sus miembros proporciona código no comprobable|
|Advertencia del compilador (nivel 4) C4960|'function' es demasiado grande para generar un perfil|
|Advertencia del compilador (nivel 1) C4961|No se combinó ningún dato de perfil en 'archivo .pgd'; se han deshabilitado las optimizaciones guiadas por perfil.|
|Advertencia del compilador (nivel 4) C4962|'función': las optimizaciones guiadas por perfil deshabilitadas porque generaban datos de perfil incoherentes|
|Advertencia del compilador (nivel 1) C4963|'*descripción*': se encontró ningún dato de perfil; se utilizaron opciones de compilador diferentes en la compilación instrumentada|
|[Advertencia del compilador (nivel 1) C4964](compiler-warning-level-1-c4964.md)|No se especificaron opciones de optimización; no se recopilará la información de perfil|
|[Advertencia del compilador (nivel 1) C4965](compiler-warning-level-1-c4965.md)|conversión boxing implícita de entero 0; Utilice nullptr o conversión explícita|
|Advertencia del compilador (nivel 1) C4966|'*función*' tiene anotación __code_seg con el nombre de segmento no compatible, anotación pasa por alto|
|C4970 de advertencia del compilador|constructor delegado: objeto de destino se omite desde '*tipo*' es estático|
|Advertencia del compilador (nivel 1) C4971|Orden de argumentos: \<objeto de destino >, \<función de destino > para el constructor delegado está en desuso, utilice \<función de destino >, \<objeto de destino = "" >|
|Advertencia del compilador (nivel 1, Error) Advertencia C4972|No se puede comprobar la modificación o el tratamiento directo del resultado de una operación de conversión unbox como valor L|
|Advertencia del compilador (nivel 1) C4973|'*símbolo*': marcado como obsoleto|
|Advertencia del compilador (nivel 1) C4974|'*símbolo*': marcado como obsoleto|
|Advertencia del compilador (nivel 3) C4981|Warbird: función '*función*' marcada como __forceinline no está entre líneas porque contiene la semántica de excepciones|
|Advertencia del compilador (nivel 3) C4985|nombre de símbolo ': atributos no presentes en la declaración anterior.|
|[Advertencia del compilador C4986](compiler-warning-c4986.md)|'*declaración*': especificación de excepción no coincide con la declaración anterior.|
|Advertencia del compilador (nivel 4) C4987|se usó una extensión no estándar: 'throw (...)'|
|Advertencia del compilador (nivel 4) C4988|'*variable*': variable declarada fuera ámbito de clase o función|
|Advertencia del compilador (nivel 4) C4989|'*tipo*': tipo tiene definiciones en conflicto.|
|Advertencia del compilador (nivel 3) C4990|Warbird: *mensaje*|
|Advertencia del compilador (nivel 3) C4991|Warbird: función '*función*' marcada como __forceinline no está entre líneas porque el nivel de protección del incluido es mayor que el elemento primario|
|Advertencia del compilador (nivel 3) C4992|Warbird: función '*función*' marcada como __forceinline no está entre líneas porque contiene código ensamblador en línea que no se puede proteger|
|[Advertencia del compilador (nivel 3) C4995](compiler-warning-level-3-c4995.md)|'función': se marcó el nombre como #pragma deprecated|
|[Advertencia del compilador (nivel 3) C4996](compiler-warning-level-3-c4996.md)|'*descripción*': *mensaje*|
|Advertencia del compilador (nivel 1) C4997|'class': la coclase no implementa una pseudointerfaz o interfaz COM|
|Advertencia del compilador (nivel 1) C4998|Error de EXPECTATIVA: *expectativa*(*valor*)|
|C4999 de advertencia del compilador|Advertencia desconocida elija el comando soporte técnico en el menú Ayuda de Visual C++, o abra el archivo de Ayuda de soporte técnico para obtener más información|
|C5022 de advertencia del compilador|'*tipo*': han especificado varios constructores de movimiento|
|C5023 de advertencia del compilador|'*tipo*': varios operadores de asignación de movimiento especificados|
|Advertencia del compilador (nivel 4) C5024|'*tipo*': mover constructor se definió implícitamente como eliminado|
|Advertencia del compilador (nivel 4) C5025|'*tipo*': mover operador de asignación se definió implícitamente como eliminado|
|Advertencia del compilador (niveles 1 y 4) C5026|'*tipo*': mover constructor se definió implícitamente como eliminado|
|Advertencia del compilador (niveles 1 y 4) C5027|'*tipo*': mover operador de asignación se definió implícitamente como eliminado|
|Advertencia del compilador (nivel 1) C5028|'*nombre*': especifica la alineación en la declaración anterior (*número*) no se especifica en la definición|
|Advertencia del compilador (nivel 4) C5029|ha utilizado una extensión no estándar: atributos de alineación en C++ que se aplican a las variables, los miembros de datos y solo los tipos de etiquetas|
|Advertencia del compilador (nivel 3) C5030|atributo '*atributo*' no se reconoce|
|Advertencia del compilador (nivel 4) C5031|#pragma warning (POP): probablemente falta de coincidencia, retirar el estado de advertencia insertado en otro archivo|
|Advertencia del compilador (nivel 4) C5032|detectado #pragma warning (Push) con ningún Warning (POP) #pragma correspondiente|
|Advertencia del compilador (nivel 1) C5033|'*clase de almacenamiento*' ya no es una clase de almacenamiento compatibles|
|C5034 de advertencia del compilador|el uso de intrínsecos '*intrínseco*' hace función *función* se compile como código de invitado|
|C5035 de advertencia del compilador|el uso de la característica '*característica*' hace función *función* se compile como código de invitado|
|Advertencia del compilador (nivel 1) C5036|varargs función de conversión de puntero cuando se compila con /hybrid:x86arm64 '*type1*'to'*type2*'|
|Advertencia del compilador C5037 (error)|'*una función miembro*': una definición fuera de línea de un miembro de una plantilla de clase no puede tener argumentos predeterminados|
