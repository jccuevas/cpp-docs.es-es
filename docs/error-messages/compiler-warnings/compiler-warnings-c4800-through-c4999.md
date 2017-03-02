---
title: Advertencias del compilador C4800 a C4999 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4806
- C4807
- C4810
- C4811
- C4812
- C4813
- C4816
- C4817
- C4822
- C4825
- C4827
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
- C4808
- C4809
dev_langs:
- C++
ms.assetid: c3182430-8b3b-4ab2-a532-5cd436707dc8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: a30a9d6a60890d0fbb4abf78df8fda4631340a6d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warnings-c4800-through-c4999"></a>Advertencias del compilador C4800 a C4999
Los artículos de esta parte de la documentación contienen información sobre un subconjunto de las advertencias del compilador de Visual C++. Puede tener acceso a información aquí o en la ventana de salida en Visual Studio, puede seleccionar un número de error y, a continuación, presione la tecla F1.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Advertencia|Mensaje|  
|-------------|-------------|  
|[Advertencia (nivel 3) del compilador C4800](../../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md)|'tipo': forzando el valor a bool 'true' o 'false' (advertencia de rendimiento)|  
|[Advertencia C4803 de compilador advertencia (nivel 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4803.md)|'método': el método raise tiene una clase de almacenamiento distinta de la del evento, 'event'|  
|[Compilador C4804 de advertencia (nivel 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4804.md)|'operación': uso no seguro del tipo 'bool' en la operación|  
|[Compilador advertencia (nivel 1) C4805](../../error-messages/compiler-warnings/compiler-warning-level-1-c4805.md)|'operación': combinación no segura del tipo 'tipo' y tipo 'tipo' en la operación|  
|Advertencia del compilador (nivel 1) C4806|'operación': operación no segura: ningún valor del tipo 'tipo' promocionado al tipo 'tipo' puede igualar la constante proporcionada|  
|Advertencia del compilador (nivel 1) C4807|'operación': combinación no segura del tipo 'tipo' y el campo de bits con signo de tipo 'tipo'|  
|Advertencia del compilador (nivel 1) C4808|Case 'valor' no es un valor válido para la condición switch de tipo 'bool'|  
|Advertencia del compilador (nivel 1) C4809|la instrucción switch tiene una etiqueta 'default' redundante; se proporcionan todas las etiquetas 'case' posibles|  
|Advertencia del compilador (nivel 1) C4810|valor de pragma pack(show) == n|  
|Advertencia del compilador (nivel 1) C4811|valor de pragma conform(forScope, show) == %s|  
|Advertencia del compilador (nivel 1) C4812|estilo de declaración obsoleto: use 'new_syntax' en su lugar|  
|Advertencia del compilador (nivel 1) C4813|'función': debe haber declarado anteriormente una función friend de una clase local|  
|Advertencia del compilador (nivel 4) C4816|'parámetro': el parámetro tiene una matriz de tamaño cero que se truncará (a menos que el objeto se pasa por referencia)|  
|Advertencia del compilador (nivel 1) C4817|'miembro': uso no válido de '.' para obtener acceso a este miembro; compilador reemplazado por '->'|  
|[Compilador advertencia (nivel 1) C4819](../../error-messages/compiler-warnings/compiler-warning-level-1-c4819.md)|El archivo contiene un carácter que no se puede representar en la página de códigos actual (número). Guarde el archivo en formato Unicode para evitar la pérdida de datos|  
|[Compilador advertencia (nivel 4) C4820](../../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md)|'bytes' bytes de relleno agregados después de construcción 'nombre_miembro'|  
|[Compilador advertencia (nivel 1) C4821](../../error-messages/compiler-warnings/compiler-warning-level-1-c4821.md)|No se puede determinar el tipo de codificación Unicode. Guarde el archivo con signatura (BOM)|  
|Advertencia del compilador (nivel 1) C4822|'función miembro': función miembro de clase local no tiene un cuerpo|  
|[Compilador advertencia (nivel 3) C4823](../../error-messages/compiler-warnings/compiler-warning-level-3-c4823.md)|'función': utiliza punteros anclados pero desenredo semántica no está habilitada. Considere el uso de /EHa|  
|Advertencia del compilador (nivel 4) C4825||  
|Advertencia del compilador (nivel 3) C4827|Un método 'ToString' público con 0 parámetros debe marcarse como virtual y override.|  
|[Compilador advertencia (nivel 1) C4829](../../error-messages/compiler-warnings/compiler-warning-level-1-c4829.md)|Parámetros posiblemente incorrectos para la función main. Considere la posibilidad de ' int main (Array\<Platform:: String ^ > ^ argv)'|  
|[Compilador advertencia (nivel 1) C4835](../../error-messages/compiler-warnings/compiler-warning-level-1-c4835.md)|'variable': el inicializador de los datos exportados no se ejecutará hasta que el código administrado se ejecuta primero en el ensamblado de host|  
|[Compilador advertencia (nivel 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md)|conversión de 'type_1' a 'type_2' requiere una conversión de restricción|  
|[Advertencia del compilador C4867](../../error-messages/compiler-warnings/compiler-warning-c4867.md)|'función': llamada de función falta la lista de argumentos; Utilice 'llamada' para crear un puntero a miembro|  
|[C4868 de advertencia del compilador](../../error-messages/compiler-warnings/compiler-warning-c4868.md)|compilador 'file(line_number)' no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicialización entre llaves|  
|Advertencia del compilador (nivel 2) C4872|se detectó una división de punto flotante por cero al compilar el gráfico de llamadas para concurrency::parallel_for_each en: '%s'|  
|Advertencia del compilador (nivel 1) C4880|realiza la conversión de 'type_1 const' a 'type_2': conversión ausente constness de un puntero o referencia puede producir un comportamiento indefinido en una función de amp restringido|  
|Advertencia del compilador (nivel 4) C4881|el constructor o destructor no se invoca para tile_static variable 'variable'|  
|Advertencia del compilador (nivel 1) C4882|la transmisión de objetos functor con operadores de llamada no constantes a concurrency::parallel_for_each está en desuso|  
|C4900 de advertencia del compilador|IL 'tool1', versión 'version1' y coinciden 'herramienta2', versión 'versión2'|  
|[Compilador advertencia (nivel 1) C4905](../../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md)|conversión de literal de cadena de tipo ancho a 'LPSTR'|  
|[Compilador advertencia (nivel 1) C4906](../../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md)|conversión de literal de cadena a 'LPWSTR'|  
|Advertencia del compilador (nivel 1) C4910|'\<identificador >: '__declspec (dllexport)' y 'extern' son incompatibles en una instancia explícita|  
|Advertencia del compilador (nivel 1) C4912|'attribute': el atributo tiene un comportamiento indefinido en un tipo definido por el usuario anidado|  
|Advertencia del compilador (nivel 4) C4913|el operador binario ',' definido por el usuario existe pero ninguna sobrecarga puede convertir todos los operandos; en su lugar, se utilizará el operador binario ',' incorporado|  
|Advertencia del compilador (nivel 1) C4916|para tener un dispid, '%$S': debe ser producido por una interfaz|  
|[Compilador advertencia (nivel 1) C4917](../../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md)|'declarador': un GUID sólo puede asociarse con una clase, interfaz o espacio de nombres|  
|Advertencia del compilador (nivel 4) C4918|'carácter': carácter no válido en la lista de optimizaciones de pragma|  
|Advertencia del compilador (nivel 1) C4920:|enum enum miembro member_1 = value_1 ya visto en enum enum como member_2 = value_2|  
|Advertencia del compilador (nivel 3) C4921|'%s': el valor de atributo '%s' no se debe especificar varias veces|  
|Advertencia del compilador (nivel 1) C4925|'method': no se puede llamar al método dispinterface desde el script|  
|Advertencia del compilador (nivel 1) C4926|'identificador': ya se ha definido el símbolo: se han omitido los atributos.|  
|[Compilador advertencia (nivel 1) C4927](../../error-messages/compiler-warnings/compiler-warning-level-1-c4927.md)|conversión no válida; se aplicó implícitamente más de una conversión definida por el usuario|  
|[Compilador advertencia (nivel 1) C4928](../../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md)|inicialización de copia no válida; se aplicó implícitamente más de una conversión definida por el usuario|  
|[Error C4929 de compilador advertencia (nivel 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4929.md)|'archivo': biblioteca de tipos contiene una unión; omitiendo el calificador 'embedded_idl'|  
|[Error C4930 de compilador advertencia (nivel 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4930.md)|'prototipo': no se llama a la función prototipo (era pensada una definición de variable?)|  
|[Compilador advertencia (nivel 4) C4931](../../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md)|se supone que la biblioteca de tipos se compiló para punteros de (número) bits|  
|Advertencia del compilador (nivel 4) Advertencia C4932|__identifier (identificador) y \_son indistinguibles _identifier(identifier)|  
|Advertencia del compilador (nivel 1) C4934|'__delegate', utilice '\__delegate' en su lugar|  
|Advertencia del compilador (nivel 1) C4935|especificador de acceso de ensamblado modificado desde 'access'|  
|Advertencia del compilador (nivel 1) Advertencia C4936|__declspec se admite solamente cuando se compila con /clr o /clr:pure|  
|Advertencia del compilador (nivel 4) C4937|'texto1' y 'texto2' no se pueden distinguir como argumentos para 'directiva'|  
|Advertencia del compilador (nivel 4) C4938|'var': variable de reducción de punto flotante puede causar resultados incoherentes bajo/fp: strict o #pragma fenv_access|  
|C4939 de advertencia del compilador|#pragma vtordisp está en desuso y se quitará en futuras versiones de Visual C++|  
|Advertencia del compilador (nivel 1) C4944|'símbolo': no se puede importar un símbolo desde 'ensamblado1': 'símbolo' ya existe en el ámbito actual|  
|[Error de compilador advertencia (nivel 1) C4945](../../error-messages/compiler-warnings/compiler-warning-level-1-c4945.md)|'símbolo': no se puede importar un símbolo desde 'ensamblado1': como 'símbolo' ya se ha importado desde otro ensamblado 'ensamblado2'|  
|[Compilador advertencia (nivel 1) C4946](../../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md)|se utilizó reinterpret_cast entre clases relacionadas: 'clase1' y 'clase2'|  
|Advertencia del compilador (nivel 1) C4947|'tipo_o_miembro': marcado como obsoleto|  
|[Compilador C4948 de advertencia (nivel 2)](../../error-messages/compiler-warnings/compiler-warning-level-2-c4948.md)|tipo de valor devuelto de 'descriptor de acceso' no coincide con el tipo último parámetro del método establecedor correspondiente|  
|[Compilador (niveles 1 y 4) C4949](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4949.md)|pragmas 'managed' y 'unmanaged' son significativos cuando se compilan con ' / clr [: opción]'|  
|Advertencia del compilador (nivel 1) C4950|'tipo_o_miembro': marcado como obsoleto|  
|C4951 de advertencia del compilador|'function' se ha editado desde que se recopilaron los datos de perfil; los datos de perfil de la función no se han utilizado|  
|C4952 de advertencia del compilador|'función': ningún perfil de datos se encuentra en la base de datos de programa 'archivo_pgd'|  
|C4953 de advertencia del compilador|Inserte 'función' se ha editado desde que se recopilaron datos, datos de perfil de perfil|  
|C4954 de advertencia del compilador|'función': no perfilado (contiene la expresión switch __int64)|  
|C4955 de advertencia del compilador|'import2': importación omitida; ya se importó desde 'import1'|  
|Advertencia del compilador (nivel 1) C4956|'tipo': este tipo no es comprobable|  
|Advertencia del compilador (nivel 1) C4957|'conversión': conversión explícita de 'cast de' a 'cast_to' no es comprobable|  
|Advertencia del compilador (nivel 1) C4958|'operación': la aritmética con punteros no es comprobable|  
|Advertencia del compilador (nivel 1) C4959|no se puede definir un tipo no administrado 'tipo' en/CLR: safe porque el acceso a sus miembros proporciona código no comprobable|  
|C4960 de advertencia del compilador|'function' es demasiado grande para generar un perfil|  
|C4961 de advertencia del compilador|No se combinó ningún dato de perfil en 'archivo .pgd'; se han deshabilitado las optimizaciones guiadas por perfil.|  
|C4962 de advertencia del compilador|'función': las optimizaciones guiadas por perfiles deshabilitadas porque generaban datos de perfil incoherentes|  
|C4963 de advertencia del compilador|%s': no hay datos de perfil se encuentra; se utilizaron opciones de compilador diferentes en la compilación instrumentada|  
|[Compilador advertencia (nivel 1) C4964](../../error-messages/compiler-warnings/compiler-warning-level-1-c4964.md)|No se especificaron opciones de optimización; no se recopilará la información de perfil|  
|[Compilador advertencia (nivel 1) C4965](../../error-messages/compiler-warnings/compiler-warning-level-1-c4965.md)|conversión boxing implícita de entero 0; utilice nullptr o conversión explícita|  
|C4966 de advertencia del compilador|'%s' tiene una anotación __code_seg con un nombre de segmento no admitido; anotación omitida|  
|C4970 de advertencia del compilador|constructor delegado: objeto de destino omitido porque '%$pS' es estático|  
|Advertencia del compilador (nivel 1) C4971|Orden de argumentos: \<objeto de destino >, \<destino función > para el constructor delegado está obsoleto, utilice \<destino función >, \<objeto de destino = "" >|  
|Advertencia del compilador (nivel 1) C4972|No se puede comprobar la modificación o el tratamiento directo del resultado de una operación de conversión unbox como valor L|  
|C4973 de advertencia del compilador|'%$S': marcado como en desuso|  
|C4974 de advertencia del compilador|'%$S': marcado como en desuso|  
|C4981 de advertencia del compilador|Warbird: la función '%$pD' marcada como __forceinline no está entre líneas porque contiene semántica de excepción|  
|Advertencia del compilador (nivel 3) C4985|nombre de símbolo ': atributos no presentan en la declaración anterior.|  
|[C4986 de advertencia del compilador](../../error-messages/compiler-warnings/compiler-warning-c4986.md)|'%$pS': la especificación de la excepción no coincide con la declaración anterior|  
|Advertencia del compilador (nivel 4) C4987|se usó una extensión no estándar: 'throw (...)'|  
|Advertencia del compilador (nivel 4) C4988|'%$S': variable declarada fuera del ámbito de clase o función|  
|C4989 de advertencia del compilador|'%s': el tipo tiene definiciones en conflicto.|  
|C4990 de advertencia del compilador|Warbird: %s|  
|C4991 de advertencia del compilador|Warbird: la función '%$pD' marcada como __forceinline no está entre líneas porque el nivel de protección de inlinee es mayor que el de su elemento primario|  
|C4992 de advertencia del compilador|Warbird: la función '%$pD' marcada como __forceinline no está entre líneas porque contiene un ensamblado alineado que no puede protegerse|  
|[Compilador advertencia (nivel 3) C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|'función': se marcó el nombre como #pragma deprecated|  
|[Compilador (nivel 3) de la advertencia C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|'%$pS': %$*|  
|Advertencia del compilador (nivel 1) C4997|'class': la coclase no implementa una pseudointerfaz o interfaz COM|  
|Advertencia del compilador (nivel 1) C4998|ERROR EN LAS EXPECTATIVAS: %s(%d)|  
|C4999 de advertencia del compilador|ADVERTENCIA DESCONOCIDA %$N Elija el comando Soporte técnico en el menú Ayuda de Visual C++ %$N o abra el archivo de ayuda de soporte técnico para obtener información|
