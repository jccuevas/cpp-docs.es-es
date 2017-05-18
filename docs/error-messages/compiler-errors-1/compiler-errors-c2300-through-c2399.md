---
title: Error del compiladors C2300 Through C2399 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
helpviewer_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
dev_langs:
- C++
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 8d8925a68ffbb7ba607e37be8db5eca33300ef23
ms.contentlocale: es-es
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-errors-c2300-through-c2399"></a>Error del compiladors C2300 Through C2399
Los artículos de esta parte de la documentación contienen información sobre una subsección de los errores del compilador de Visual C++. Puede tener acceso a información aquí o bien, en la ventana de **salida** de Visual Studio, puede seleccionar un número de error y elegir después la tecla F1.  
  
> [!NOTE]
>  No todos [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] error está documentado en MSDN. En muchos casos, el mensaje de diagnóstico proporciona toda la información que está disponible. Si cree que un mensaje de error necesita una explicación adicional, puede enviarnos su opinión. Puede utilizar el formulario de comentarios de esta página, o vaya a la barra de menús de Visual Studio y elija **ayuda**, **notificar un error**, o puede enviar un informe de sugerencia o un error en [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Puede encontrar ayuda adicional sobre errores y advertencias en los foros públicos de MSDN. El [lenguaje Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) es foro para preguntas y debate sobre el [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] sintaxis del lenguaje y compilador. El [General de Visual C++](http://go.microsoft.com/fwlink/?LinkId=158194) es foro para preguntas sobre [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] que no se debaten en otros foros. También puede encontrar ayuda sobre los errores y advertencias en [desbordamiento de la pila](http://stackoverflow.com/).  
  
|Error|Mensaje|  
|-----------|-------------|  
|[Error del compilador C2300](compiler-error-c2300.md)|'*clase*': clase no tiene un destructor denominado ' ~*clase*'|  
|[Error del compilador C2301](compiler-error-c2301.md)|izquierdo de ' -> ~*identificador*' debe señalar a class/struct/union|  
|[Error del compilador C2302](compiler-error-c2302.md)|izquierdo de '. ~*identificador*' debe tener el tipo class/struct/union|  
|C2303 de Error del compilador|No se puede usar el control de excepciones estructurado en un corrutina|  
|C2304 de Error del compilador|'*palabra clave*' no se puede usar dentro de un bloque catch|  
|C2305 de Error del compilador|'*archivo*' no contiene información de depuración para este módulo|  
|C2306 de Error del compilador|'*archivo*' no contiene la información de depuración más reciente para este módulo|  
|[Error del compilador C2307](compiler-error-c2307.md)|pragma *directiva* se debe mover fuera de la función si la compilación incremental está habilitada|  
|[Error del compilador C2308](compiler-error-c2308.md)|concatenación de cadenas no coincidentes|  
|[Error del compilador C2309](compiler-error-c2309.md)|el controlador de tipo catch esperaba una declaración de excepción entre paréntesis|  
|[Error del compilador C2310](compiler-error-c2310.md)|los controladores de tipo catch deben especificar un tipo|  
|[Error del compilador C2311](compiler-error-c2311.md)|'*tipo*': ha sido detectado por '...' en línea *número*|  
|[Error del compilador C2312](compiler-error-c2312.md)|'*type1*': ha sido detectado por '*type2*' en línea *número*|  
|[Error del compilador C2313](compiler-error-c2313.md)|'*type1*': se detecta por referencia ('*type2*') en línea *número*|  
|C2314 de Error del compilador|palabra clave '*palabraclave1*' está en desuso: utilice '*palabraclave2*' en su lugar|  
|[Error del compilador C2315](compiler-error-c2315.md)|'*type1*': referencia ha sido detectada por '*type2*' en línea *número*|  
|[Error del compilador C2316](compiler-error-c2316.md)|'*tipo*': no se puede detectar porque el destructor o al constructor de copias se inaccesible o se ha eliminado|  
|[Error del compilador C2317](compiler-error-c2317.md)|'try' bloque empieza en la línea '*número*' no tiene ningún controladores catch|  
|[Error del compilador C2318](compiler-error-c2318.md)|no hay ningún bloque try asociado a este controlador de tipo catch|  
|[Error del compilador C2319](compiler-error-c2319.md)|'try/catch' debe ir seguido de una instrucción compuesta. Falta '{'|  
|[Error del compilador C2320](compiler-error-c2320.md)|se esperaba ':' a continuación del especificador de acceso '*especificador*'|  
|C2321 de Error del compilador|'*identificador*' es una palabra clave y no se puede usar en este contexto|  
|[Error del compilador C2322](compiler-error-c2322.md)|'*identificador*': la dirección de dllimport '*identificador*' no es estático|  
|C2323 de Error del compilador|'*identificador*': operador no miembro new o delete funciones pueden no declararse estáticas o en un espacio de nombres distinto del espacio de nombres global|  
|[Error del compilador C2324](compiler-error-c2324.md)|'*identificador*': no se esperaba a la derecha de ':: ~'|  
|[Error del compilador C2325](compiler-error-c2325.md)|'*type1*': tipo no esperado a la derecha de ' -> ~': se esperaba '*type2*'|  
|[Error del compilador C2326](compiler-error-c2326.md)|'*declarador*': no se puede obtener acceso la función '*identificador*'|  
|[Error del compilador C2327](compiler-error-c2327.md)|'*identificador*': no es un nombre de tipo, estático o enumerador|  
|C2328 de Error del compilador|'*palabra clave*': no se admite todavía (palabra clave)|  
|C2329 de Error del compilador|'*identificador*': __ptr64 no está disponible para punteros a funciones|  
|C2330 de Error del compilador|'implementation_key( )' solo es válida en una región delimitada por #pragma start_map_region/stop_map_region|  
|C2331 de Error del compilador|el acceso a '*identificador*"ahora está definido como"*accessibility1*', previamente se definió para ser'*accessibility2*'|  
|[Error del compilador C2332](compiler-error-c2332.md)|'*typedef*': falta el nombre de etiqueta|  
|[Error del compilador C2333](compiler-error-c2333.md)|'*función*': error en la declaración de función; omitiendo el cuerpo de la función|  
|[Error del compilador C2334](compiler-error-c2334.md)|tokens inesperados anteriores '*token*'; se omitirá el cuerpo de función aparente|  
|C2335 de Error del compilador|'*identificador*': un tipo no se incluirán en una lista de parámetros de función|  
|C2336 de Error del compilador|'*tipo*': tipo no válido|  
|[Error del compilador C2337](compiler-error-c2337.md)|'*atributo*': no se encontró el atributo|  
|[Error del compilador C2338](compiler-error-c2338.md)|*(mensaje de error de proveedor externo)*|  
|C2339 de Error del compilador|'*identificador*': tipo no válido en IDL incrustado|  
|C2340 de Error del compilador|'*identificador*': 'static' solo puede usarse dentro de una definición de clase|  
|[Error del compilador C2341](compiler-error-c2341.md)|'*sección*': se debe definir el segmento utilizando #pragma data_seg, code_seg o sección anterior para usar|  
|C2342 de Error del compilador|error de sintaxis: calificadores de tipo conflictivos|  
|C2343 de Error del compilador|'*sección*': atributos de sección incompatibles|  
|[Error del compilador C2344](compiler-error-c2344.md)|Alinear (*número*): alineación debe ser potencia de dos|  
|[Error del compilador C2345](compiler-error-c2345.md)|Alinear (*número*): valor de alineación no válido|  
|[Error del compilador C2346](compiler-error-c2346.md)|'*función*' no se pueden compilar como nativo: '*explicación*'|  
|C2347 de Error del compilador|Obsoleto.|  
|[Error del compilador C2348](compiler-error-c2348.md)|'*tipo*': no es un agregado de estilo C, no se puede exportar en IDL incrustado|  
|[Error del compilador C2349](compiler-error-c2349.md)|'*función*' no se pueden compilar como administrado: '*explicación*'; Utilice #pragma no administrado|  
|[Error del compilador C2350](compiler-error-c2350.md)|'*identificador*' no es un miembro estático|  
|[Error del compilador C2351](compiler-error-c2351.md)|sintaxis de inicialización del constructor de C++ obsoleta|  
|[Error del compilador C2352](compiler-error-c2352.md)|'*identificador*': llamada no válida de función miembro no estática|  
|[Error del compilador C2353](compiler-error-c2353.md)|no se permite la especificación de excepciones|  
|C2354 de Error del compilador|Obsoleto.|  
|[Error del compilador C2355](compiler-error-c2355.md)|'this': solo se puede hacer referencia a this en funciones miembro no estáticas o inicializadores de miembro de datos no estáticos|  
|[Error del compilador C2356](compiler-error-c2356.md)|el segmento de inicialización no debe cambiar durante la unidad de traducción|  
|[Error del compilador C2357](compiler-error-c2357.md)|'*identificador*': debe ser una función de tipo '*tipo*'|  
|C2358 de Error del compilador|'*identificador*': no se puede definir una propiedad estática fuera de una definición de clase|  
|C2359 de Error del compilador|Obsoleto.|  
|[Error del compilador C2360](compiler-error-c2360.md)|inicialización de '*identificador*' se omite en la etiqueta 'case'|  
|[Error del compilador C2361](compiler-error-c2361.md)|inicialización de '*identificador*' se omite en la etiqueta 'default'|  
|[Error del compilador C2362](compiler-error-c2362.md)|inicialización de '*identificador*' se omite en ' goto *etiqueta*'|  
|C2363 de Error del compilador|función de límite numérico intrínseco del compilador requiere un argumento de literal de cadena|  
|[Error del compilador C2364](compiler-error-c2364.md)|'*tipo*': tipo no válido para el atributo personalizado|  
|[Error del compilador C2365](compiler-error-c2365.md)|'*member1*': nueva definición; definición anterior era '*member2*'|  
|C2366 de Error del compilador|'*identificador*': nueva definición; especificadores implementation_key distintos|  
|C2367 de Error del compilador|Obsoleto.|  
|[Error del compilador C2368](compiler-error-c2368.md)|'*identificador*': nueva definición; especificadores de asignación distintos|  
|[Error del compilador C2369](compiler-error-c2369.md)|'*identificador*': nueva definición; subíndices distintos|  
|[Error del compilador C2370](compiler-error-c2370.md)|'*identificador*': nueva definición; clase de almacenamiento distinta|  
|[Error del compilador C2371](compiler-error-c2371.md)|'*identificador*': nueva definición; tipos básicos distintos|  
|[Error del compilador C2372](compiler-error-c2372.md)|'*identificador*': nueva definición; tipos distintos de direccionamiento indirecto|  
|[Error del compilador C2373](compiler-error-c2373.md)|'*identificador*': nueva definición; modificadores de tipo distintos|  
|[Error del compilador C2374](compiler-error-c2374.md)|'*identificador*': nueva definición; inicialización múltiple|  
|[Error del compilador C2375](compiler-error-c2375.md)|'*identificador*': redefinición; vinculación distinta|  
|[Error del compilador C2376](compiler-error-c2376.md)|'*identificador*': nueva definición; distinta asignación con base|  
|[Error del compilador C2377](compiler-error-c2377.md)|'*identificador*': nueva definición; typedef no se puede sobrecargar con ningún otro símbolo|  
|[Error del compilador C2378](compiler-error-c2378.md)|'*identificador*': nueva definición; no se pueden sobrecargar el símbolo con typedef|  
|[Error del compilador C2379](compiler-error-c2379.md)|parámetro formal *número* tiene un tipo diferente cuando promueve|  
|[Error del compilador C2380](compiler-error-c2380.md)|tipos que preceden '*identificador*' (¿constructor con tipo de valor devuelto o redefinición no válida de nombre de clase actual?)|  
|[Error del compilador C2381](compiler-error-c2381.md)|'*identificador*': nueva definición; '__declspec (noreturn)' o '[[noreturn]]' difiere|  
|[Error del compilador C2382](compiler-error-c2382.md)|'*identificador*': nueva definición; especificaciones de excepción diferentes|  
|[Error del compilador C2383](compiler-error-c2383.md)|'*identificador*': no se permiten argumentos predeterminados en este símbolo|  
|[Error del compilador C2384](compiler-error-c2384.md)|'*miembro*': no se puede aplicar thread_local o __declspec (Thread) a un miembro de una clase administrada o WinRT|  
|[Error del compilador C2385](compiler-error-c2385.md)|acceso ambiguo de '*miembro*'|  
|[Error del compilador C2386](compiler-error-c2386.md)|'*identificador*': ya existe un símbolo con este nombre en el ámbito actual|  
|[Error del compilador C2387](compiler-error-c2387.md)|'*identificador*': clase base ambigua|  
|[Error del compilador C2388](compiler-error-c2388.md)|'*identificador*': un símbolo no se puede declarar con __declspec (AppDomain) y __declspec (proceso)|  
|[Error del compilador C2389](compiler-error-c2389.md)|'*operador*': operando no válido 'nullptr'|  
|[Error del compilador C2390](compiler-error-c2390.md)|'*identificador*': clase de almacenamiento incorrecta*especificador*'|  
|[Error del compilador C2391](compiler-error-c2391.md)|'*identificador*': 'friend' no se puede usar durante la definición de tipo|  
|[Error del compilador C2392](compiler-error-c2392.md)|'*member1*': valor devueltos de covariante no se admiten tipos en tipos administrados o WinRT, de lo contrario '*member2*' se reemplazaría|  
|[Error del compilador C2393](compiler-error-c2393.md)|'*símbolo*': símbolo por appdomain no se puede asignar en el segmento '*segmento*'|  
|[Error del compilador C2394](compiler-error-c2394.md)|'*tipo*:: operador *operador*': operador CLR o WinRT no es válido. Al menos un parámetro debe ser de los siguientes tipos: ' t ^', ' t ^ %', ' t ^ &', donde T = '*tipo*'|  
|[Error del compilador C2395](compiler-error-c2395.md)|'*tipo*:: operador *operador*': operador CLR o WinRT no es válido. Al menos un parámetro debe ser de los siguientes tipos: ' t ', ' t %', ' t &', ' t ^', ' t ^ %', ' t ^ &', donde T = '*tipo*'|  
|[Error del compilador C2396](compiler-error-c2396.md)|'*type1*:: operador *type2*': función de conversión definida por el usuario CLR o WinRT no es válido. Debe convertir de o convertir en: ' t ^', ' t ^ %', ' t ^ &', donde T = '*type1*'|  
|[Error del compilador C2397](compiler-error-c2397.md)|conversión de '*type1*'to'*type2*' requiere una conversión de restricción|  
|C2398 de Error del compilador|Elemento '*número*': conversión de '*type1*'to'*type2*' requiere una conversión de restricción|  
|C2399 de Error del compilador|Obsoleto.|  

