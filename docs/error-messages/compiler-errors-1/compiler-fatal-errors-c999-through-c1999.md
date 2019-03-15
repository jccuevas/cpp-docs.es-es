---
title: 'Errores graves del compilador: de C999 a C1999'
ms.date: 11/17/2017
f1_keywords:
- C1012
- C1013
- C1014
- C1016
- C1018
- C1019
- C1020
- C1021
- C1022
- C1023
- C1034
- C1035
- C1036
- C1037
- C1038
- C1041
- C1045
- C1047
- C1048
- C1049
- C1053
- C1063
- C1068
- C1069
- C1070
- C1074
- C1077
- C1082
- C1086
- C1087
- C1088
- C1089
- C1090
- C1091
- C1098
- C1099
- C1100
- C1101
- C1102
- C1103
- C1104
- C1105
- C1108
- C1109
- C1110
- C1111
- C1112
- C1114
- C1190
- C1193
- C1195
- C1196
- C1201
- C1202
- C1205
- C1206
- C1207
- C1208
- C1209
- C1210
- C1211
- C1300
- C1301
- C1302
- C1306
- C1310
- C1312
- C1352
- C1353
- C1383
- C1384
- C1451
- C1505
- C1508
- C1510
- C1852
- C1901
- C1903
- C1904
helpviewer_keywords:
- C1012
- C1013
- C1014
- C1016
- C1018
- C1019
- C1020
- C1021
- C1022
- C1023
- C1034
- C1035
- C1036
- C1037
- C1038
- C1041
- C1045
- C1047
- C1048
- C1049
- C1053
- C1063
- C1068
- C1069
- C1070
- C1074
- C1077
- C1082
- C1086
- C1087
- C1088
- C1089
- C1090
- C1091
- C1098
- C1099
- C1100
- C1101
- C1102
- C1103
- C1104
- C1105
- C1108
- C1109
- C1110
- C1111
- C1112
- C1114
- C1190
- C1193
- C1195
- C1196
- C1201
- C1202
- C1205
- C1206
- C1207
- C1208
- C1209
- C1210
- C1211
- C1300
- C1301
- C1302
- C1306
- C1310
- C1312
- C1352
- C1353
- C1383
- C1384
- C1451
- C1505
- C1508
- C1510
- C1852
- C1901
- C1903
ms.assetid: 6c8df109-7594-48ed-987a-97d9fe2b04af
ms.openlocfilehash: 1159a635f0c7a61e591b4d96c4e55bd2baf44782
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814454"
---
# <a name="compiler-fatal-errors-c999-through-c1999"></a>Errores graves del compilador: de C999 a C1999

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error irrecuperable C999](../../error-messages/compiler-errors-1/fatal-error-c999.md)|MENSAJE DESCONOCIDO Elija el comando Soporte técnico en el menú Ayuda de Visual C++, o abra el archivo de ayuda Soporte técnico para obtener más información|
|[Error irrecuperable C1001](../../error-messages/compiler-errors-1/fatal-error-c1001.md)|Error interno en el compilador.<br /><br /> Archivo del compilador '*file*', línea *number*<br /><br /> Para solucionar este problema, intente simplificar o cambiar el programa en aquellas líneas próximas a las ubicaciones que se enumeran a continuación. Elija el comando Soporte técnico en el menú Ayuda de Visual C++ o abra el archivo de ayuda de soporte técnico para obtener más información|
|[Error irrecuperable C1002](../../error-messages/compiler-errors-1/fatal-error-c1002.md)|el compilador no tiene espacio en el montón en el paso 2|
|[Error irrecuperable C1003](../../error-messages/compiler-errors-1/fatal-error-c1003.md)|el recuento de errores supera *number*; se detiene la compilación|
|[Error irrecuperable C1004](../../error-messages/compiler-errors-1/fatal-error-c1004.md)|se encontró un final de archivo no esperado|
|[Error irrecuperable C1005](../../error-messages/compiler-errors-1/fatal-error-c1005.md)|cadena demasiado grande para el búfer|
|[Error irrecuperable C1007](../../error-messages/compiler-errors-1/fatal-error-c1007.md)|marca '*string*' irreconocible en '*option*'|
|[Error irrecuperable C1008](../../error-messages/compiler-errors-1/fatal-error-c1008.md)|no se ha especificado un archivo de entrada|
|[Error irrecuperable C1009](../../error-messages/compiler-errors-1/fatal-error-c1009.md)|límite del compilador: las macros están demasiado anidadas|
|[Error irrecuperable C1010](../../error-messages/compiler-errors-1/fatal-error-c1010.md)|final de archivo inesperado al buscar la directiva de encabezado precompilado. ¿Olvidó agregar ' #include <*archivo*>' para el origen?|
|Error irrecuperable C1012|Paréntesis '*character*' desemparejado.|
|Error irrecuperable C1013|límite del compilador: hay demasiados paréntesis abiertos|
|Error irrecuperable C1014|hay demasiados archivos de inclusión: nivel = *number*|
|Error irrecuperable C1016|#ifdef/#ifndef esperaba un identificador|
|[Error irrecuperable C1017](../../error-messages/compiler-errors-1/fatal-error-c1017.md)|expresión constante de tipo entero no válida|
|Error irrecuperable C1018|#elif inesperada|
|Error irrecuperable C1019|#else inesperada|
|Error irrecuperable C1020|#endif inesperada|
|Error irrecuperable C1021|comando de preprocesador '*string*' no válido|
|Error irrecuperable C1022|se esperaba #endif|
|Error irrecuperable C1023|'*file*': error inesperado con pch; recompile pch|
|[Error irrecuperable C1026](../../error-messages/compiler-errors-1/fatal-error-c1026.md)|desbordamiento de la pila del analizador, programa demasiado complejo|
|[Error irrecuperable C1033](../../error-messages/compiler-errors-1/fatal-error-c1033.md)|no se puede abrir la base de datos de programa '*file*'|
|Error irrecuperable C1034|*file*: no se ha establecido ninguna ruta de acceso de inclusión|
|Error irrecuperable C1035|expresión demasiado compleja; simplifique la expresión|
|Error irrecuperable C1036|no se puede sobrescribir el formato de base de datos del programa anterior, elimine '*file*' y vuelva compilar|
|Error irrecuperable C1037|no se puede abrir el archivo objeto '*file*'|
|Error irrecuperable C1038|límite del compilador: '*function*': el estado de flujo de control es demasiado complejo; simplifique la función|
|Error irrecuperable C1041|no puede abrir la base de datos de programa '*file*'. Si varios CL.EXE escriben en el mismo archivo .PDB, use /FS.|
|Error irrecuperable C1045|límite del compilador: las especificaciones de vinculación están demasiado anidadas|
|[Error irrecuperable C1046](../../error-messages/compiler-errors-1/fatal-error-c1046.md)|límite del compilador: *structure* está demasiado anidado|
|Error irrecuperable C1047|El objeto o el archivo de biblioteca '*file*' se creó con un compilador anterior a otros objetos; recompile las bibliotecas y los objetos antiguos|
|Error irrecuperable C1048|opción '*string*' desconocida en '*option*'|
|Error irrecuperable C1049|argumento numérico*value*' no válido|
|[Error irrecuperable C1051](../../error-messages/compiler-errors-1/fatal-error-c1051.md)|el archivo de base de datos de programa, '*file*', tiene un formato obsoleto; elimínelo y vuelva a compilar|
|[Error irrecuperable C1052](fatal-error-c1052.md)|archivo de base de datos de programa, '*filename*', fue generado por el vinculador con/debug: Fastlink; compilador no puede actualizar estos archivos PDB; elimínelo o utilice /Fd para especificar otro nombre de archivo PDB|
|Error irrecuperable C1053|'*function*': la función es demasiado larga|
|[Error irrecuperable C1054](../../error-messages/compiler-errors-1/fatal-error-c1054.md)|límite del compilador: los inicializadores están demasiado anidados|
|[Error irrecuperable C1055](../../error-messages/compiler-errors-1/fatal-error-c1055.md)|límite del compilador: no hay claves|
|[Error irrecuperable C1057](../../error-messages/compiler-errors-1/fatal-error-c1057.md)|final de archivo inesperado en la expansión de macros|
|[Error irrecuperable C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)|espacio de montón insuficiente en el compilador|
|[Error irrecuperable C1061](../../error-messages/compiler-errors-1/fatal-error-c1061.md)|límite del compilador: los bloques están demasiado anidados|
|Error irrecuperable C1063|límite del compilador: desbordamiento de la pila del compilador|
|[Error irrecuperable C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)|límite del compilador: desbordamiento de símbolo (token) de búfer interno|
|[Error irrecuperable C1065](../../error-messages/compiler-errors-1/fatal-error-c1065.md)|límite del compilador: no hay etiquetas|
|[Error irrecuperable C1067](../../error-messages/compiler-errors-1/fatal-error-c1067.md)|límite del compilador: Se superó el límite de 64K de tamaño de un tipo de registro|
|Error irrecuperable C1068|no se puede abrir el archivo '*file*'|
|Error irrecuperable C1069|no se puede leer la línea de comandos del compilador|
|Error irrecuperable C1070|el par #if/#endif no coincide en el archivo '*file*'|
|[Error irrecuperable C1071](../../error-messages/compiler-errors-1/fatal-error-c1071.md)|no se esperaba el final de archivo encontrado en el comentario|
|[Error irrecuperable C1073](../../error-messages/compiler-errors-1/fatal-error-c1073.md)|Error interno que requiere compilación incremental(archivo del compilador '*file*', línea *number*)|
|Error irrecuperable C1074|'IDB' es una extensión no válida para el archivo PDB: *file*|
|[Error irrecuperable C1075](../../error-messages/compiler-errors-1/fatal-error-c1075.md)|el elemento *token* de la izquierda estaba sin asignar al final del archivo|
|[Error irrecuperable C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)|límite del compilador: se ha alcanzado el límite del montón interno; utilice /Zm para especificar un límite más alto|
|Error irrecuperable C1077|límite del compilador: no se pueden tener más de *number* opciones de la línea de comandos|
|[Error irrecuperable C1079](../../error-messages/compiler-errors-1/fatal-error-c1079.md)|límite del compilador: Límite de tamaño de archivo PCH superado|
|[Error irrecuperable C1080](../../error-messages/compiler-errors-1/fatal-error-c1080.md)|límite del compilador: la opción de la línea de comandos ha superado el límite de *number* caracteres|
|[Error irrecuperable C1081](../../error-messages/compiler-errors-1/fatal-error-c1081.md)|'*file*': nombre de archivo demasiado largo|
|Error irrecuperable C1082|no se puede cerrar el archivo *type* : '*file*': *message*|
|[Error irrecuperable C1083](../../error-messages/compiler-errors-1/fatal-error-c1083.md)|No se puede abrir el archivo *type* : '*file*': *message*|
|[Error irrecuperable C1084](../../error-messages/compiler-errors-1/fatal-error-c1084.md)|No se puede leer el archivo *type* : '*file*': *message*|
|[Error irrecuperable C1085](../../error-messages/compiler-errors-1/fatal-error-c1085.md)|No se puede escribir en el archivo *type* : '*file*': *message*|
|Error irrecuperable C1086|No se puede buscar en el archivo *type* : '*file*': *message*|
|Error irrecuperable C1087|No se puede indicar al archivo *type* : '*file*': *message*|
|Error irrecuperable C1088|No se puede vaciar el archivo *type* : '*file*': *message*|
|Error irrecuperable C1089|No se puede truncar el archivo *type* : '*file*': *message*|
|Error irrecuperable C1090|Error al llamar a la API de PDB, código de error '*code*': '*message*'|
|Error irrecuperable C1091|límite del compilador: la longitud de la cadena supera los *number* bytes|
|[Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)|La función Editar y continuar no admite cambios en los tipos de datos; se requiere compilación|
|[Error irrecuperable C1093](../../error-messages/compiler-errors-1/fatal-error-c1093.md)|La llamada API '*function*' produjo un error '*HRESULT*' : '*description*'|
|[Error irrecuperable C1094](../../error-messages/compiler-errors-1/fatal-error-c1094.md)|'-Zm*number*': la opción de la línea de comandos no es coherente con el valor utilizado para generar el encabezado precompilado ('-Zm*number*')|
|Error irrecuperable C1098|No coincide la versión con el motor de la función Editar y continuar|
|Error irrecuperable C1099|El motor de la función Editar y continuar está deteniendo la compilación|
|Error irrecuperable C1100|no se puede inicializar OLE: *error*|
|Error irrecuperable C1101|no se puede crear un controlador para el atributo '*identifier*'|
|Error irrecuperable C1102|no se puede inicializar: *error*|
|Error irrecuperable C1103|error irrecuperable al importar el id. de programa: '*message*'|
|Error irrecuperable C1104|error irrecuperable al importar el libid: '*message*'|
|Error irrecuperable C1105|*message*: *error*|
|[Error irrecuperable C1107](../../error-messages/compiler-errors-1/fatal-error-c1107.md)|no se encuentra el ensamblado '*assembly*': especifique la ruta de acceso de búsqueda del ensamblado utilizando /AI o estableciendo la variable de entorno LIBPATH|
|Error irrecuperable C1108|no se puede encontrar la DLL: '*file*'|
|Error irrecuperable C1109|no se puede encontrar '*symbol*' en la DLL '*file*'|
|Error irrecuperable C1110|hay demasiadas definiciones template/generic anidadas|
|Error irrecuperable C1111|hay demasiados parámetros template/generic|
|Error irrecuperable C1112|límite del compilador: `'number`' demasiados argumentos de macro, solo se permite ' *number* '|
|[Error irrecuperable C1113](../../error-messages/compiler-errors-1/fatal-error-c1113.md)|error de #using en '*file*'|
|Error irrecuperable C1114|'*archivo*': WinRT no admite #using de un ensamblado administrado|
|[Error irrecuperable C1120](../../error-messages/compiler-errors-1/fatal-error-c1120.md)|error al llamar a GetProcAddress debido a '*function*'|
|[Error irrecuperable C1121](../../error-messages/compiler-errors-1/fatal-error-c1121.md)|no se pudo llamar a CryptoAPI|
|[Error irrecuperable C1126](../../error-messages/compiler-errors-1/fatal-error-c1126.md)|la asignación automática supera *size*|
|[Error irrecuperable C1128](../../error-messages/compiler-errors-1/fatal-error-c1128.md)|el número de secciones superó el límite de formato de archivo de objeto: compile con /bigobj|
|[Error irrecuperable C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md)|#error: *message*|
|Error irrecuperable C1190|un código de destino administrado requiere una opción '/clr'|
|[Error irrecuperable C1191](../../error-messages/compiler-errors-1/fatal-error-c1191.md)|'*file*' solo se puede importar en un ámbito global|
|[Error irrecuperable C1192](../../error-messages/compiler-errors-1/fatal-error-c1192.md)|error de #using en '*file*'|
|Error irrecuperable C1193|no se ha obtenido un error esperado en *file*(*line*)|
|Error irrecuperable C1195|el uso de /Yu y /Yc en la misma línea de comandos no es compatible con la opción /clr|
|Error irrecuperable C1196|'*identifier*': el identificador encontrado en la biblioteca de tipos '*typelib*' no es un identificador de C++ válido|
|[Error irrecuperable C1197](../../error-messages/compiler-errors-1/fatal-error-c1197.md)|no se puede hacer referencia a '*file*' porque el programa ya hacía referencia a '*file*'|
|Error irrecuperable C1201|no se puede continuar después del error de sintaxis en la definición de plantilla de clase|
|Error irrecuperable C1202|contexto de tipo recursivo o de dependencia de función demasiado complejos|
|Error irrecuperable C1205|La versión del runtime instalada no admite elementos genéricos|
|Error irrecuperable C1206|La versión del runtime instalada no admite datos por Appdomain|
|Error irrecuperable C1207|Plantillas administradas no admitidas por la versión del runtime instalada|
|Error irrecuperable C1208|La versión del runtime instalada no admite la asignación de clases de referencia en la pila|
|Error irrecuperable C1209|Ensamblados de confianza no admitidos por la versión del runtime instalada|
|Error irrecuperable C1210|La versión del runtime instalada no admite /clr:pure ni /clr:safe|
|Error irrecuperable C1211|La versión del runtime instalada no admite el atributo personalizado TypeForwardedTo|
|Error irrecuperable C1300|error al tener acceso a la base de datos del programa *file* (*message*)|
|Error irrecuperable C1301|error al tener acceso a la base de datos del programa *file*, formato no válido; elimine y recompile|
|Error irrecuperable C1302|no hay datos de perfil para el módulo '*module*' en la base de datos del perfil '*file*'|
|[Error irrecuperable C1305](../../error-messages/compiler-errors-1/fatal-error-c1305.md)|la base de datos del perfil '*file*' es para una arquitectura diferente|
|Error irrecuperable C1306|el último cambio en la base de datos de perfil '*file*' no fue un análisis de optimización; puede que las decisiones de optimización no estén actualizadas|
|[Error irrecuperable C1307](../../error-messages/compiler-errors-1/fatal-error-c1307.md)|el programa se ha editado desde que se recogieron los datos de perfil|
|[Error irrecuperable C1308](../../error-messages/compiler-errors-1/fatal-error-c1308.md)|*file*: no se admite la vinculación de ensamblados|
|[Error irrecuperable C1309](../../error-messages/compiler-errors-1/fatal-error-c1309.md)|Las versiones de C2.DLL y pgodb*ver*.DLL no coinciden|
|Error irrecuperable C1310|las optimizaciones guiadas por perfiles no están disponibles con OpenMP|
|[Error irrecuperable C1311](../../error-messages/compiler-errors-1/fatal-error-c1311.md)|El formato COFF no puede inicializar estáticamente '*symbol*' con *number* bytes de una dirección|
|Error irrecuperable C1312|Demasiadas bifurcaciones condicionales en la función.  Simplifique o refactorice el código fuente.|
|[Error irrecuperable C1313](../../error-messages/compiler-errors-1/fatal-error-c1313.md)|límite del compilador: los bloques *type* no se pueden anidar más de *number* niveles.|
|[Error irrecuperable C1350](../../error-messages/compiler-errors-1/fatal-error-c1350.md)|error al cargar la DLL '*file*': no se encontró la DLL|
|[Error irrecuperable C1351](../../error-messages/compiler-errors-1/fatal-error-c1351.md)|error al cargar la DLL '*file*': versión incompatible|
|Error irrecuperable C1352|MSIL no válido o dañado en la función '*function*' del módulo '*module*'|
|Error irrecuperable C1353|no se pudo realizar la operación de metadatos: el runtime no está instalado o la versión no coincide|
|[Error irrecuperable C1382](../../error-messages/compiler-errors-1/fatal-error-c1382.md)|el archivo PCH '*file*' se ha recompilado desde que se creó '*obj*'. Recompile este objeto|
|Error irrecuperable C1383|la opción /GL del compilador es incompatible con la versión instalada de Common Language Runtime|
|Error irrecuperable C1384|Valor incorrecto de PGO_PATH_TRANSLATION al vincular '*file*'|
|Error irrecuperable C1451|No se pudo generar información de depuración al compilar el gráfico de llamadas para concurrency::parallel_for_each en: '*callsite*'|
|Error irrecuperable C1505|error irrecuperable de búsqueda anticipada del analizador|
|[Error irrecuperable C1506](../../error-messages/compiler-errors-1/fatal-error-c1506.md)|error irrecuperable de ámbito de bloque|
|Error irrecuperable C1508|límite del compilador: '*function*': más de 65535 bytes de argumentos|
|[Error irrecuperable C1509](../../error-messages/compiler-errors-1/fatal-error-c1509.md)|límite del compilador: hay demasiados estados de controlador de excepciones en la función '*function*'. Simplifique la función|
|[Error irrecuperable C1510](../../error-messages/compiler-errors-1/fatal-error-c1510.md)|No se puede abrir el archivo clui.dll de recursos de idioma|
|[Error irrecuperable C1601](../../error-messages/compiler-errors-1/fatal-error-c1601.md)|código de operación de ensamblado alineado no admitido|
|[Error irrecuperable C1602](../../error-messages/compiler-errors-1/fatal-error-c1602.md)|intrínseco no admitido|
|[Error irrecuperable C1603](../../error-messages/compiler-errors-1/fatal-error-c1603.md)|destino de bifurcación de ensamblado alineado fuera de intervalo en *number* bytes|
|Error irrecuperable C1852|'*file*' no es un archivo de encabezado precompilado válido|
|[Error irrecuperable C1853](../../error-messages/compiler-errors-1/fatal-error-c1853.md)|El archivo de encabezado precompilado '*file*' es de una versión anterior del compilador, o bien el encabezado precompilado es de C++ y lo está utilizando desde C (o viceversa)|
|[Error irrecuperable C1854](../../error-messages/compiler-errors-1/fatal-error-c1854.md)|no se puede sobrescribir la información realizada durante la creación del encabezado precompilado en el archivo objeto: '*file*'|
|[Error irrecuperable C1900](../../error-messages/compiler-errors-1/fatal-error-c1900.md)|Il '*tool*', versión '*number*', no coincide con '*tool*', versión '*number*'|
|Error irrecuperable C1901|Error interno de administración de memoria|
|[Error irrecuperable C1902](../../error-messages/compiler-errors-1/fatal-error-c1902.md)|El administrador de base de datos de programa no coincide; compruebe la instalación|
|Error irrecuperable C1903|no se puede recuperar de errores anteriores; se detiene la compilación|
|Error irrecuperable C1904|interacción con el proveedor incorrecta: '*file*'|
|[Error irrecuperable C1905](../../error-messages/compiler-errors-1/fatal-error-c1905.md)|Front-end y back-end no compatibles (el destino debe ser el mismo procesador).|