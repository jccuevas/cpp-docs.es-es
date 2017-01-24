---
title: "Advertencias del compilador desactivadas de forma predeterminada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "cl.exe (compilador), establecer opciones"
  - "advertencias, compilador"
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
caps.latest.revision: 39
caps.handback.revision: 37
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencias del compilador desactivadas de forma predeterminada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El compilador incluye advertencias que están desactivadas de forma predeterminada porque la mayoría de los usuarios no desean verlas.  Sin embargo, puede habilitar estas advertencias mediante una de las opciones siguientes.  
  
 `#pragma warning(default :`  `warning_number` `)`  
 La advertencia especificada \(`warning_number`\) se habilita en su nivel predeterminado.  La documentación de la advertencia contiene el nivel predeterminado de la advertencia.  
  
 `#pragma warning(` `warning_level`  `:`  `warning_number` `)`  
 La advertencia especificada \(`warning_number`\) se habilita en el nivel especificado \(`warning_level`\).  
  
 [\/Wall](../build/reference/compiler-option-warning-level.md)  
 **\/Wall** habilita todas las advertencias que están desactivadas de forma predeterminada.  
  
 Las siguientes advertencias están deshabilitadas de forma predeterminada.  
  
|||  
|-|-|  
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) \(nivel 4\)|el enumerador 'identificador' en una instrucción switch de la enumeración 'enumeración' no está controlada de forma explícita por una etiqueta de caso|  
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) \(nivel 3\)|el enumerador 'identificador' en una instrucción switch de la enumeración 'enumeración' no está controlado|  
|C4191 \(nivel 3\)|'operador\/operación': conversión no segura de 'tipo de expresión' a 'tipo necesario'|  
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) \(nivel 4\)|'identificador': conversión de 'tipo1' a 'tipo2', posible pérdida de datos|  
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) \(nivel 4\)|'operador': conversión de 'tipo1' a 'tipo2', posible pérdida de datos|  
|[C4255](../Topic/Compiler%20Warning%20\(level%204\)%20C4255.md) \(nivel 4\)|'función': no se ha proporcionado un prototipo de función: convirtiendo '\(\)' a '\(void\)'|  
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) \(nivel 4\)|'función': la función miembro no reemplaza ninguna función miembro virtual de clase base|  
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) \(nivel 1\)|'función\_virtual': no hay un reemplazo disponible para la función miembro virtual desde 'clase' base; la función está oculta|  
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) \(nivel 3\)|'clase': la clase tiene funciones virtuales, pero el destructor no es virtual|  
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) \(nivel 4\)|'función': no hay un reemplazo disponible para la función miembro virtual del 'tipo' base; la función está oculta|  
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) \(nivel 3\)|'operador': no coinciden las constantes sin signo o negativas|  
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) \(nivel 4\)|se ha utilizado una extensión no estándar : 'var' : la variable de control de bucles declarada en el bucle For se utiliza fuera del ámbito del bucle For|  
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) \(nivel 4\)|'operador': la expresión siempre es false|  
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) \(nivel 2\)|'conversión': truncamiento de 'tipo1' a 'tipo2'|  
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) \(nivel 1\)|'variable' : truncamiento de puntero de 'tipo' a 'tipo'|  
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) \(nivel 1\)|'operación' : conversión de 'tipo1' a 'tipo2' de mayor tamaño|  
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) \(nivel 4\)|'tipo': se detectó el uso de un tipo no definido en los metadatos CLR; el uso de este tipo puede provocar una excepción en tiempo de ejecución|  
|[C4342](../Topic/Compiler%20Warning%20\(level%201\)%20C4342.md) \(nivel 1\)|cambio en el comportamiento: se llamó a 'función', pero en versiones anteriores se llamaba a un operador de miembro|  
|[C4350](../Topic/Compiler%20Warning%20\(level%201\)%20C4350.md) \(nivel 1\)|cambio de comportamiento: se llamó a 'miembro1' en lugar de a 'miembro2'|  
|[C4355](../Topic/Compiler%20Warning%20C4355.md)|'this': utilizado en la lista de inicializadores de miembro base|  
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) \(nivel 4\)|'acción': conversión de 'type\_1' a 'type\_2', no coinciden signed\/unsigned|  
|C4370 \(nivel 3\)|el diseño de clase cambió desde una versión anterior del compilador debido a una mejora del empaquetado|  
|C4371 \(nivel 3\)|el diseño de clase puede haber cambiado desde una versión anterior del compilador debido a una mejora del empaquetado del miembro 'miembro'|  
|C4388 \(nivel 4\)|no coinciden signed\/unsigned|  
|[C4412](../Topic/Compiler%20Warning%20\(level%202\)%20C4412.md) \(nivel 2\)|'función': la firma de la función contiene el tipo 'tipo'; no es seguro pasar los objetos de C\+\+ entre código puro y mixto o nativo|  
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) \(nivel 4\)|falta el especificador de tipo; se presupone int.  Nota: C no admite default\-int|  
|[C4435](../Topic/Compiler%20Warning%20\(level%204\)%20C4435.md) \(nivel 4\)|'clase1': La distribución de objetos de \/vd2 cambiará debido a la base virtual 'clase2'|  
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) \(nivel 4\)|es posible que se produzca un error de dynamic\_cast de 'clase1' base virtual a 'clase2' en algunos contextos|  
|C4444 \(nivel 3\)|el nivel superior '\_\_unaligned' no está implementado en este contexto|  
|C4471 \(nivel 4\)|una declaración adelantada de una enumeración sin ámbito debe tener un tipo subyacente \(se presupone int\)|  
|C4472 \(nivel 1\)|“identificador” es una enumeración nativa: agregue un especificador de acceso \(privado\/público\) para declarar una enumeración administrada|  
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) \(nivel 4\)|'función': se ha quitado la función inline a la que no se hace referencia|  
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) \(nivel 4\)|'nombre de tipo': el nombre de tipo supera el límite de metadatos de 'limite' caracteres|  
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) \(nivel 1\)|la expresión antes de la coma se evalúa como una función a la que le falta una lista de argumentos|  
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) \(nivel 1\)|falta la lista de argumentos de la llamada de función antes de la coma|  
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) \(nivel 1\)|'operador': un operador antes de una coma no tiene ningún efecto; se esperaba un operador con efectos secundarios|  
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) \(nivel 1\)|la expresión antes de la coma no tiene ningún efecto; se esperaba una expresión con efectos secundarios|  
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) \(nivel 1\)|'operador': un operador antes de una coma no tiene ningún efecto; ¿realmente pensaba en 'operador'?|  
|[C4555](../Topic/Compiler%20Warning%20\(level%201\)%20C4555.md) \(nivel 1\)|la expresión no tiene efecto; se esperaba una expresión con efecto secundario|  
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) \(nivel 3\)|'\_\_assume' contiene el efecto 'efecto'|  
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) \(nivel 4\)|Información: la semántica de catch\(…\) cambió desde Visual C\+\+ 7.1; ya no se detectan excepciones estructuradas \(SEH\)|  
|C4574 \(nivel 4\)|'identificador' se ha definido como '0': ¿pretendía usar '\#if identificador'?|  
|C4608 \(nivel 3\)|'symbol1' ya ha sido inicializado por otro miembro union en la lista de inicializadores, 'symbol2'|  
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) \(nivel 3\)|\#pragma warning: no existe el número de advertencia 'número'|  
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) \(nivel 4\)|'clase derivada': no se puede generar el constructor predeterminado porque no se puede obtener acceso a un constructor predeterminado de clase base|  
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) \(nivel 4\)|'clase derivada': no se puede generar el constructor de copias porque no se puede obtener acceso a un constructor de copias de clase base|  
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) \(nivel 4\)|'clase derivada': no se puede generar el operador de asignaciones porque no se puede obtener acceso a un operador de asignaciones de clase base|  
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) \(nivel 1\)|los digramas no son compatibles con \-Ze.  La secuencia de caracteres 'digrama' no interpretado como token alternativo de 'char'|  
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) \(nivel 3\)|'instancia': la construcción del objeto estático local no es segura para subprocesos|  
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) \(nivel 4\)|'símbolo' no está definido como macro de preprocesador y se reemplaza por '0' para 'directivas'|  
|C4682 \(nivel 4\)|'símbolo': no se ha especificado un atributo de parámetro direccional; se establecerá \[in\] como predeterminado|  
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) \(nivel 3\)|'tipo definido por el usuario': posible cambio de comportamiento, cambio en la convención de llamada devuelta definida por el usuario|  
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) \(nivel 1\)|'función': la firma de un miembro no privado contiene un tipo nativo privado de ensamblado 'tipo\_nativo'|  
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) \(nivel 4\)|'función': la función no está entre líneas|  
|[C4738](../Topic/Compiler%20Warning%20\(Level%203\)%20C4738.md) \(nivel 3\)|almacenando el resultado flotante de 32 bits en memoria; posible pérdida de rendimiento|  
|C4767 \(nivel 4\)|el nombre de sección 'símbolo' tiene más de 8 caracteres y lo truncará el vinculador|  
|C4786 \(nivel 3\)|'símbolo': el nombre de objeto se ha truncado a 'número' caracteres en la información de depuración|  
|[C4820](../Topic/Compiler%20Warning%20\(level%204\)%20C4820.md) \(nivel 4\)|'bytes' bytes de relleno agregados después de construcción 'nombre\_miembro'|  
|[C4826](../error-messages/compiler-warnings/compiler-warning-level-2-c4826.md) \(nivel 2\)|La conversión de 'tipo1' a 'tipo2' produce una extensión de signo.  Esto puede provocar un comportamiento en tiempo de ejecución inesperado|  
|[C4837](../error-messages/compiler-warnings/compiler-warning-level-4-c4837.md) \(nivel 4\)|se detectó un trígrafo: '??%c' reemplazado por '%c'|  
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) \(nivel 1\)|conversión de literal de cadena de tipo ancho a 'LPSTR'|  
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) \(nivel 1\)|conversión de literal de cadena a 'LPWSTR'|  
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) \(nivel 1\)|'declarador': un GUID se puede asociar únicamente a una clase, interfaz o espacio de nombres|  
|[C4928](../Topic/Compiler%20Warning%20\(level%201\)%20C4928.md) \(nivel 1\)|inicialización de copia no válida; se aplicó implícitamente más de una conversión definida por el usuario|  
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) \(nivel 4\)|se supone que la biblioteca de tipos se compiló para punteros de \(número\) bits|  
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) \(nivel 1\)|se utilizó reinterpret\_cast entre clases relacionadas: 'clase1' y 'clase2'|  
|C4962|'función': se han deshabilitado las optimizaciones guiadas por perfil porque generaban datos de perfil incoherentes|  
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) \(nivel 4\)|'símbolo': la especificación de la excepción no coincide con la declaración anterior|  
|C4987 \(nivel 4\)|se usó una extensión no estándar: 'throw \(...\)'|  
|C4988 \(nivel 4\)|'símbolo': variable declarada fuera del ámbito de clase o función|  
  
## Vea también  
 [warning](../preprocessor/warning.md)