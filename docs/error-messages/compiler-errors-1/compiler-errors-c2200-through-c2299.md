---
title: Errores del compilador de C2200 a C2299
ms.date: 04/21/2019
f1_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
helpviewer_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
ms.assetid: 9b36d11b-9510-4390-96f1-0c9235124d14
ms.openlocfilehash: 5af97ab46a97d3019abcc937cc0a74c5f865a9ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360520"
---
# <a name="compiler-errors-c2200-through-c2299"></a>Errores del compilador de C2200 a C2299

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C2200](compiler-error-c2200.md)|'*función*': función ya se ha definido.|
|[Error del compilador C2201](compiler-error-c2201.md)|'*identificador*': debe tener una vinculación externa para exportarlo o importarlo|
|Error del compilador C2202|'*función*': no todas las rutas de acceso de control devuelven un valor|
|[Error del compilador C2203](compiler-error-c2203.md)|Eliminar operador no puede especificar límites de matriz|
|[Error del compilador C2204](compiler-error-c2204.md)|'*tipo*': se encuentra dentro de los paréntesis de definición de tipo|
|[Error del compilador C2205](compiler-error-c2205.md)|'*identificador*': no se puede inicializar variables extern con ámbito de bloque|
|[Error del compilador C2206](compiler-error-c2206.md)|'*función*': typedef no se puede usar para la definición de función|
|[Error del compilador C2207](compiler-error-c2207.md)|'*miembro*': un miembro de una plantilla de clase no puede adquirir un tipo de función|
|[Error del compilador C2208](compiler-error-c2208.md)|'*tipo*': no han definido miembros utilizando este tipo|
|Error del compilador C2209|'*identificador*': no se puede usar alias en las declaraciones de constructor|
|Error del compilador C2210|'*identificador*': las expansiones del paquete no se puede usar como argumentos a parámetros sin empaquetar de plantillas de alias|
|Error del compilador C2211|Un destructor no virtual en una clase ref derivado de una clase ref con un destructor público también debe ser público|
|[Error del compilador C2212](compiler-error-c2212.md)|'*identificador*': __based no está disponible para punteros a funciones|
|[Error del compilador C2213](compiler-error-c2213.md)|'*identificador*': argumento para __based no válido|
|Error del compilador C2214|los punteros basados en 'void' requieren el uso de: >|
|Error del compilador C2215|'*palabra clave*' no se puede usar con ' / arch: SSE'|
|[Error del compilador C2216](compiler-error-c2216.md)|'*palabraclave1*'no se puede usar con'*palabraclave2*'|
|[Error del compilador C2217](compiler-error-c2217.md)|'*attribute1*'requiere'*atributo2*'|
|[Error del compilador C2218](compiler-error-c2218.md)|'*calltype*' no se puede usar con ' / arch: IA32'|
|[Error del compilador C2219](compiler-error-c2219.md)|error de sintaxis: calificador de tipo debe ser posterior a ' *'|
|[Error del compilador C2220](compiler-error-c2220.md)|Advertencia tratada como error - no '*filetype*' archivo generado|
|Error del compilador C2221|Obsoleto.|
|[Error del compilador C2222](compiler-error-c2222.md)|tipo inesperado '*tipo*': se esperaba una clase base o miembro|
|[Error del compilador C2223](compiler-error-c2223.md)|operando izquierdo de ' ->*identificador*' debe señalar a struct/union|
|[Error del compilador C2224](compiler-error-c2224.md)|operando izquierdo de '. *identificador*' debe tener el tipo struct/union|
|Error del compilador C2225|Obsoleto.|
|[Error del compilador C2226](compiler-error-c2226.md)|error de sintaxis: tipo inesperado '*tipo*'|
|[Error del compilador C2227](compiler-error-c2227.md)|operando izquierdo de ' ->*identificador*' debe señalar al tipo de clase/struct/union/generic|
|[Error del compilador C2228](compiler-error-c2228.md)|operando izquierdo de '. *identificador*' debe tener clase/struct/union|
|[Error del compilador C2229](compiler-error-c2229.md)|clase/struct/union '*tipo*' tiene una matriz de tamaño cero no válida|
|Error del compilador C2230|no se pudo encontrar el módulo '*nombre*'|
|[Error del compilador C2231](compiler-error-c2231.md)|'. *identificador*': operando izquierdo señala a 'class/struct/union', use '->'|
|[Error del compilador C2232](compiler-error-c2232.md)|' ->*identificador*': operando izquierdo tiene ' class/struct/union ' tipo'.' use|
|[Error del compilador C2233](compiler-error-c2233.md)|'*identificador*': las matrices de objetos que contienen matrices de tamaño cero no son válidas|
|[Error del compilador C2234](compiler-error-c2234.md)|*identificador*': las matrices de referencias no son válidas|
|Error del compilador C2235|Obsoleto.|
|[Error del compilador C2236](compiler-error-c2236.md)|token inesperado '*token*'. Compruebe si olvidó un ';'|
|Error del compilador C2237|declaración de módulo múltiple|
|[Error del compilador C2238](compiler-error-c2238.md)|tokens inesperados anterior '*token*'|
|Error del compilador C2239|'*función*': si intenta eliminar una función __declspec (dllexport)|
|Error del compilador C2240|Obsoleto.|
|[Error del compilador C2241](compiler-error-c2241.md)|'*identificador*': el acceso a miembros está restringido|
|[Error del compilador C2242](compiler-error-c2242.md)|un nombre typedef no puede seguir a class/struct/union|
|[Error del compilador C2243](compiler-error-c2243.md)|'*conversion_type*': conversión de '*type1*'para'*type2*' existe, pero es inaccesible|
|[Error del compilador C2244](compiler-error-c2244.md)|'*identificador*': no se puede hacer coincidir la definición de función con una declaración existente|
|[Error del compilador C2245](compiler-error-c2245.md)|función miembro inexistente '*función*' especificada como friend (la firma de la función miembro no coincide con ninguna sobrecarga)|
|[Error del compilador C2246](compiler-error-c2246.md)|'*identificador*': miembro de datos estático no válido en la clase definida localmente|
|[Error del compilador C2247](compiler-error-c2247.md)|'*identificador*' no es accesible porque '*class1*'usos'*especificador*' para heredar de'*class2*'|
|[Error del compilador C2248](compiler-error-c2248.md)|'*identificador*': no se puede obtener acceso a *accesibilidad* *miembro* declarado en la clase*clase*'|
|[Error del compilador C2249](compiler-error-c2249.md)|'*identificador*': ninguna ruta accesible a *accesibilidad* *miembro* declarado en la base virtual '*clase*'|
|[Error del compilador C2250](compiler-error-c2250.md)|'*identificador*': herencia ambigua de *clase*::*miembro*'|
|[Error del compilador C2251](compiler-error-c2251.md)|espacio de nombres '*espacio de nombres*'no tiene un miembro'*identificador*': ¿pretendía utilizar '*miembro*'?|
|[Error del compilador C2252](compiler-error-c2252.md)|creación de instancias explícita de una plantilla solo puede aparecer en el ámbito del espacio de nombres|
|[Error del compilador C2253](compiler-error-c2253.md)|'*función*': el especificador puro o invalidación abstracto solo se permite en la función virtual|
|[Error del compilador C2254](compiler-error-c2254.md)|'*función*': el especificador puro o invalidación abstracto no se permite en la función friend|
|[Error del compilador C2255](compiler-error-c2255.md)|'*elemento*': no se permite fuera de una definición de clase|
|[Error del compilador C2256](compiler-error-c2256.md)|uso no válido de especificador friend en '*función*'|
|Error del compilador C2257|'*especificador*': no se permite en el tipo de valor devuelto final|
|[Error del compilador C2258](compiler-error-c2258.md)|sintaxis pura no válida, debe ser '= 0'|
|[Error del compilador C2259](compiler-error-c2259.md)|'*clase*': no se puede crear una instancia de clase abstracta|
|Error del compilador C2260|'*especificador*': especificador de ensamblado de confianza InternalsVisibleToAttribute no válido|
|[Error del compilador C2261](compiler-error-c2261.md)|'*cadena*': referencia de ensamblado no es válida y no se puede resolver|
|[Error del compilador C2262](compiler-error-c2262.md)|'*especificador*': Las declaraciones InternalsVisibleTo no pueden tener una versión, referencia cultural o arquitectura de procesador|
|Error del compilador C2263|Obsoleto.|
|[Error del compilador C2264](compiler-error-c2264.md)|'*función*': error en la declaración o definición de función; la función llamada no|
|Error del compilador C2265|Obsoleto.|
|[Error del compilador C2266](compiler-error-c2266.md)|'*identificador*': referencia a una matriz delimitada que no sea constante no es válida|
|[Error del compilador C2267](compiler-error-c2267.md)|'*función*': las funciones static con ámbito de bloque no son válidas|
|[Error del compilador C2268](compiler-error-c2268.md)|'*función*' es una auxiliar de biblioteca predefinida para el compilador. Aplicaciones auxiliares de biblioteca no se admiten con/GL; Compile el archivo objeto '*filename*' sin/GL.|
|Error del compilador C2269|no se puede crear un puntero o referencia a un tipo de función cualificado (requiere el puntero a miembro)|
|[Error del compilador C2270](compiler-error-c2270.md)|'*función*': modificadores no permitidos en funciones no miembro|
|[Error del compilador C2271](compiler-error-c2271.md)|'*función*': new o delete no puede tener modificadores de lista formales|
|[Error del compilador C2272](compiler-error-c2272.md)|'*función*': modificadores no permitidos en funciones miembro static|
|[Error del compilador C2273](compiler-error-c2273.md)|'*tipo*': no es válido como lado derecho del operador '->'|
|[Error del compilador C2274](compiler-error-c2274.md)|'*tipo*': no es válido como lado derecho de '.' operador|
|[Error del compilador C2275](compiler-error-c2275.md)|'*tipo*': uso no válido de este tipo como una expresión.|
|[Error del compilador C2276](compiler-error-c2276.md)|'*operador*': operación no válida en la expresión de función miembro enlazada|
|[Error del compilador C2277](compiler-error-c2277.md)|'*función*': no se puede adquirir la dirección de esta función miembro|
|Error del compilador C2278|Obsoleto.|
|[Error del compilador C2279](compiler-error-c2279.md)|especificación de excepción no puede aparecer en una declaración typedef|
|[Error del compilador C2280](compiler-error-c2280.md)|'*clase*::*función*': intentando hacer referencia a una función eliminada|
|Error del compilador C2281|'*clase*::*función*': solo se puede eliminar una función en la primera declaración|
|Error del compilador C2282|'*función1*'no puede invalidar'*función2*'|
|[Error del compilador C2283](compiler-error-c2283.md)|'*identificador*': el especificador puro o invalidación abstracto no se permite en la clase/estructura sin nombre|
|Error del compilador C2284|'*función*': argumento no válido para la función intrínseca, parámetro *número*|
|[Error del compilador C2285](compiler-error-c2285.md)|punteros a la representación de los miembros ya se ha determinado - se ha omitido pragma|
|[Error del compilador C2286](compiler-error-c2286.md)|punteros a miembros de '*identificador*' representación ya está establecida en *herencia* -se omite la declaración|
|[Error del compilador C2287](compiler-error-c2287.md)|'*identificador*': representación de herencia: '*inheritiance*'es menos general que el requerido'*herencia*'|
|Error del compilador C2288|Obsoleto.|
|[Error del compilador C2289](compiler-error-c2289.md)|el mismo calificador de tipo se ha utilizado más de una vez|
|[Error del compilador C2290](compiler-error-c2290.md)|Omitidas la sintaxis C++ 'asm'. Use __asm.|
|Error del compilador C2291|No se puede exportar un espacio de nombres anónimo.|
|[Error del compilador C2292](compiler-error-c2292.md)|'*identificador*': representación de herencia de mejor caso: *inheritance1*' declarado pero '*y herencia 2*' necesario|
|[Error del compilador C2293](compiler-error-c2293.md)|'*identificador*': no se puede tener una variable miembro como especificador __based|
|Error del compilador C2294|no se puede exportar el símbolo '*identificador*' porque tiene vinculación interna|
|[Error del compilador C2295](compiler-error-c2295.md)|caracteres de escape '*carácter*': no es válido en la definición de macro|
|[Error del compilador C2296](compiler-error-c2296.md)|'*operador*': operando no es válido; el izquierdo tiene el tipo '*tipo*'|
|[Error del compilador C2297](compiler-error-c2297.md)|'*operador*': operando no es válido; tiene el tipo '*tipo*'|
|[Error del compilador C2298](compiler-error-c2298.md)|llamada perdida a puntero a función miembro|
|[Error del compilador C2299](compiler-error-c2299.md)|'*función*': cambio de comportamiento: una especialización explícita no puede ser un constructor de copias o el operador de asignación de copia|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
