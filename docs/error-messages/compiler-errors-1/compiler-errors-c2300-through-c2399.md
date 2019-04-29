---
title: Errores del compilador de C2300 a C2399
ms.date: 04/21/2019
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
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
ms.openlocfilehash: 28ab73857b46fed29e2ba8d7bc051ffb81b54bb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360455"
---
# <a name="compiler-errors-c2300-through-c2399"></a>Errores del compilador de C2300 a C2399

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C2300](compiler-error-c2300.md)|'*clase*': clase no tiene un destructor denominado ' ~*clase*'|
|[Error del compilador C2301](compiler-error-c2301.md)|operando izquierdo de ' -> ~*identificador*' debe apuntar a la clase/struct/union|
|[Error del compilador C2302](compiler-error-c2302.md)|operando izquierdo de '. ~*identificador*' debe tener el tipo de clase/struct/union|
|Error del compilador C2303|No se puede utilizar el control de excepciones estructurado en una corrutina|
|Error del compilador C2304|'*palabra clave*' no se puede usar dentro de un bloque catch|
|Error del compilador C2305|'*archivo*' no contiene información de depuración para este módulo|
|Error del compilador C2306|'*archivo*' no contiene la información de depuración más reciente para este módulo|
|[Error del compilador C2307](compiler-error-c2307.md)|pragma *directiva* se deben mover fuera de la función si la compilación incremental está habilitada|
|[Error del compilador C2308](compiler-error-c2308.md)|concatenación de cadenas no coincidentes|
|[Error del compilador C2309](compiler-error-c2309.md)|controlador de tipo catch esperaba una declaración de excepción entre paréntesis|
|[Error del compilador C2310](compiler-error-c2310.md)|controladores catch deben especificar un tipo|
|[Error del compilador C2311](compiler-error-c2311.md)|'*tipo*': ha sido detectada por '...' en la línea *número*|
|[Error del compilador C2312](compiler-error-c2312.md)|'*type1*': ha sido detectada por '*type2*' en línea *número*|
|[Error del compilador C2313](compiler-error-c2313.md)|'*type1*': ha sido detectada por referencia ('*type2*') en línea *número*|
|Error del compilador C2314|palabra clave '*palabraclave1*' está en desuso: utilice '*palabraclave2*' en su lugar|
|[Error del compilador C2315](compiler-error-c2315.md)|'*type1*': referencia ha sido detectada por '*type2*' en línea *número*|
|[Error del compilador C2316](compiler-error-c2316.md)|'*tipo*': no se puede detectar porque el destructor o constructor de copia es inaccesibles o eliminados|
|[Error del compilador C2317](compiler-error-c2317.md)|'try' bloque empieza en la línea '*número*' no tiene controladores catch|
|[Error del compilador C2318](compiler-error-c2318.md)|no hay ningún bloque try asociado a este controlador de tipo catch|
|[Error del compilador C2319](compiler-error-c2319.md)|'try/catch' debe ir seguido de una instrucción compuesta. Falta '{'|
|[Error del compilador C2320](compiler-error-c2320.md)|se esperaba ':' a continuación del especificador de acceso '*especificador*'|
|Error del compilador C2321|'*identificador*' es una palabra clave y no se puede usar en este contexto|
|[Error del compilador C2322](compiler-error-c2322.md)|'*identificador*': la dirección de dllimport '*identificador*' no es estático|
|Error del compilador C2323|'*identificador*': operador no miembro new o delete funciones no pueden declararse estáticas o en un espacio de nombres distinto del espacio de nombres global|
|[Error del compilador C2324](compiler-error-c2324.md)|'*identificador*': no se esperaba a la derecha de ':: ~'|
|[Error del compilador C2325](compiler-error-c2325.md)|'*type1*': tipo no esperado a la derecha de ' -> ~': se esperaba '*type2*'|
|[Error del compilador C2326](compiler-error-c2326.md)|'*declarador*': no se puede obtener acceso la función '*identificador*'|
|[Error del compilador C2327](compiler-error-c2327.md)|'*identificador*': no es un nombre de tipo, estático o enumerador|
|Error del compilador C2328|'*palabra clave*': no se admite aún la palabra clave|
|Error del compilador C2329|'*identificador*': __ptr64 no está disponible para punteros a funciones|
|Error del compilador C2330|'implementation_key ()' solo es válido en una región delimitada por #pragma start_map_region/stop_map_region|
|Error del compilador C2331|el acceso a '*identificador*'ahora define como'*accessibility1*', previamente se ha definido como'*accessibility2*'|
|[Error del compilador C2332](compiler-error-c2332.md)|'*typedef*': falta el nombre de etiqueta|
|[Error del compilador C2333](compiler-error-c2333.md)|'*función*': error en la declaración de función; se omitirá el cuerpo de la función|
|[Error del compilador C2334](compiler-error-c2334.md)|tokens inesperados anterior '*token*'; se omitirá el cuerpo de función aparente|
|Error del compilador C2335|'*identificador*': un tipo no se pueden introducir en una lista de parámetros de función|
|Error del compilador C2336|'*tipo*': tipo no válido|
|[Error del compilador C2337](compiler-error-c2337.md)|'*atributo*': no se encontró el atributo|
|[Error del compilador C2338](compiler-error-c2338.md)|*(mensaje de error de proveedor externo)*|
|Error del compilador C2339|'*identificador*': tipo no válido en IDL incrustado|
|Error del compilador C2340|'*identificador*': 'static' solo puede usarse dentro de una definición de clase|
|[Error del compilador C2341](compiler-error-c2341.md)|'*sección*': se debe definir el segmento utilizando #pragma data_seg, code_seg o la sección anterior para usar|
|Error del compilador C2342|error de sintaxis: calificadores de tipo conflictivos|
|Error del compilador C2343|'*sección*': atributos de sección conflictivos|
|[Error del compilador C2344](compiler-error-c2344.md)|Alinear (*número*): alineación debe ser potencia de dos|
|[Error del compilador C2345](compiler-error-c2345.md)|Alinear (*número*): valor de alineación no válido|
|[Error del compilador C2346](compiler-error-c2346.md)|'*función*' no se puede compilar como nativa: '*explicación*'|
|Error del compilador C2347|Obsoleto.|
|[Error del compilador C2348](compiler-error-c2348.md)|'*tipo*': no es un agregado de estilo C, no se puede exportar en IDL incrustado|
|[Error del compilador C2349](compiler-error-c2349.md)|'*función*' no se puede compilar como administrada: '*explicación*'; Utilice #pragma no administrado|
|[Error del compilador C2350](compiler-error-c2350.md)|'*identificador*' no es un miembro estático|
|[Error del compilador C2351](compiler-error-c2351.md)|sintaxis de inicialización de constructor de C++ obsoleta|
|[Error del compilador C2352](compiler-error-c2352.md)|'*identificador*': llamada no válida de función miembro no estática|
|[Error del compilador C2353](compiler-error-c2353.md)|no se permite la especificación de excepción|
|Error del compilador C2354|Obsoleto.|
|[Error del compilador C2355](compiler-error-c2355.md)|'this': sólo se puede hacer referencia dentro de las funciones miembro no estáticas o inicializadores de miembro de datos no estáticos|
|[Error del compilador C2356](compiler-error-c2356.md)|el segmento de inicialización no debe cambiar durante la unidad de traducción|
|[Error del compilador C2357](compiler-error-c2357.md)|'*identificador*': debe ser una función de tipo '*tipo*'|
|Error del compilador C2358|'*identificador*': no se puede definir una propiedad estática fuera de una definición de clase|
|Error del compilador C2359|Obsoleto.|
|[Error del compilador C2360](compiler-error-c2360.md)|inicialización de '*identificador*' se omite en la etiqueta 'case'|
|[Error del compilador C2361](compiler-error-c2361.md)|inicialización de '*identificador*' se omite en la etiqueta 'default'|
|[Error del compilador C2362](compiler-error-c2362.md)|inicialización de '*identificador*' se omite en ' goto *etiqueta*'|
|Error del compilador C2363|función de límite numérico intrínseco del compilador requiere un argumento literal de cadena|
|[Error del compilador C2364](compiler-error-c2364.md)|'*tipo*': tipo no válido para el atributo personalizado|
|[Error del compilador C2365](compiler-error-c2365.md)|'*member1*': redefinición; la definición anterior era '*member2*'|
|Error del compilador C2366|'*identifier*': redefinition; different implementation_key specifiers|
|Error del compilador C2367|Obsoleto.|
|[Error del compilador C2368](compiler-error-c2368.md)|'*identificador*': nueva definición; especificadores de asignación distintos|
|[Error del compilador C2369](compiler-error-c2369.md)|'*identificador*': nueva definición; subíndices distintos|
|[Error del compilador C2370](compiler-error-c2370.md)|'*identificador*': nueva definición; clase de almacenamiento distinta|
|[Error del compilador C2371](compiler-error-c2371.md)|'*identificador*': nueva definición; tipos básicos distintos|
|[Error del compilador C2372](compiler-error-c2372.md)|'*identificador*': nueva definición; distintos tipos de direccionamiento indirecto|
|[Error del compilador C2373](compiler-error-c2373.md)|'*identificador*': nueva definición; modificadores de tipo distintos|
|[Error del compilador C2374](compiler-error-c2374.md)|'*identificador*': nueva definición; inicialización múltiple|
|[Error del compilador C2375](compiler-error-c2375.md)|'*identificador*': redefinición; vinculación distinta|
|[Error del compilador C2376](compiler-error-c2376.md)|'*identificador*': nueva definición; distinta asignación con base|
|[Error del compilador C2377](compiler-error-c2377.md)|'*identificador*': nueva definición; typedef no se puede sobrecargar con ningún otro símbolo|
|[Error del compilador C2378](compiler-error-c2378.md)|'*identificador*': nueva definición; no se puede sobrecargar el símbolo con typedef|
|[Error del compilador C2379](compiler-error-c2379.md)|parámetro formal *número* tiene tipo diferente tras promoverlo|
|[Error del compilador C2380](compiler-error-c2380.md)|tipos que preceden '*identificador*' (¿constructor con tipo de valor devuelto o redefinición no válida de nombre de clase actual?)|
|[Error del compilador C2381](compiler-error-c2381.md)|'*identificador*': redefinición; '__declspec (noreturn)' o '[[noreturn]]' difiere|
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
|[Error del compilador C2392](compiler-error-c2392.md)|'*member1*': valor devueltos de covariante tipos no se admiten en tipos administrados o WinRT, de lo contrario '*member2*' se reemplazaría|
|[Error del compilador C2393](compiler-error-c2393.md)|'*símbolo*': símbolo por appdomain no se puede asignar en el segmento '*segmento*'|
|[Error del compilador C2394](compiler-error-c2394.md)|'*tipo*:: operador *operador*': Operador CLR o WinRT no es válido. Debe ser al menos un parámetro de los siguientes tipos:  ' T ^', ' t ^ %', ' t ^ &', donde T = '*tipo*'|
|[Error del compilador C2395](compiler-error-c2395.md)|'*tipo*:: operador *operador*': Operador CLR o WinRT no es válido. Debe ser al menos un parámetro de los siguientes tipos: ' T ', ' t %', ' t &', ' t ^', ' t ^ %', ' t ^ &', donde T = '*tipo*'|
|[Error del compilador C2396](compiler-error-c2396.md)|'*type1*:: operador *type2*': Función de conversión definido por el usuario CLR o WinRT no es válida. Debe convertir de o convertir en: ' T ^', ' t ^ %', ' t ^ &', donde T = '*type1*'|
|[Error del compilador C2397](compiler-error-c2397.md)|conversión de '*type1*'para'*type2*' requiere una conversión de restricción|
|Error del compilador C2398|Elemento '*número*': conversión de '*type1*'para'*type2*' requiere una conversión de restricción|
|Error del compilador C2399|Obsoleto.|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
