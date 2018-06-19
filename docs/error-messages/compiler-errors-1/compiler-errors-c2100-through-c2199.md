---
title: Errores del compilador C2100 through C2199 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
helpviewer_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
dev_langs:
- C++
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f276776028fde88e4ef1e4559f0dd4db08abfe03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237143"
---
# <a name="compiler-errors-c2100-through-c2199"></a>Error del compiladors C2100 through C2199

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C2100](compiler-error-c2100.md)|direccionamiento indirecto no válido|
|[Error del compilador C2101](compiler-error-c2101.md)|'&' en la constante|
|[Error del compilador C2102](compiler-error-c2102.md)|'&' requiere valor L|
|[Error del compilador C2103](compiler-error-c2103.md)|'&' en la variable de registro|
|[Error del compilador C2104](compiler-error-c2104.md)|' &' en el campo de bits que se pasa por alto|
|[Error del compilador C2105](compiler-error-c2105.md)|'*operador*' necesita l-value|
|[Error del compilador C2106](compiler-error-c2106.md)|'*operador*': operando izquierdo debe ser l-value|
|[Error del compilador C2107](compiler-error-c2107.md)|índice no válido, direccionamiento indirecto no permitido|
|[Error del compilador C2108](compiler-error-c2108.md)|el subíndice no es de tipo entero|
|[Error del compilador C2109](compiler-error-c2109.md)|subíndice requiere el tipo de puntero o matriz|
|[Error del compilador C2110](compiler-error-c2110.md)|'+': no se puede agregar dos punteros|
|[Error del compilador C2111](compiler-error-c2111.md)|'+': suma de punteros requiere un operando de entero|
|[Error del compilador C2112](compiler-error-c2112.md)|'-': resta de punteros requiere un operando entero o puntero|
|[Error del compilador C2113](compiler-error-c2113.md)|'-': puntero solo se pueda restar de otro puntero|
|[Error del compilador C2114](compiler-error-c2114.md)|'*operador*': puntero a la izquierda; el valor entero de necesidades de derecha|
|[Error del compilador C2115](compiler-error-c2115.md)|'*operador*': tipos incompatibles|
|[Error del compilador C2116](compiler-error-c2116.md)|las listas de parámetros de función son distintas|
|[Error del compilador C2117](compiler-error-c2117.md)|'*identificador*': desbordamiento de límites de matriz|
|[Error del compilador C2118](compiler-error-c2118.md)|subíndice negativo|
|C2119 de Error del compilador|'*identificador*': el tipo de '*tipo*' no se puede deducir de un inicializador vacío|
|[Error del compilador C2120](compiler-error-c2120.md)|'void' no es válido con todos los tipos|
|[Error del compilador C2121](compiler-error-c2121.md)|'#': carácter no válido: posiblemente el resultado de una expansión de macro|
|[Error del compilador C2122](compiler-error-c2122.md)|'*identificador*': parámetro de prototipo en permitido de lista de nombre|
|C2123 de Error del compilador|'*identificador*': las plantillas de alias no se puede especializar explícitamente o parcialmente|
|[Error del compilador C2124](compiler-error-c2124.md)|división (normal o módulo) por cero|
|C2125 de Error del compilador|'constexpr' no es compatible con '*token*'|
|C2126 de Error del compilador|'*identificador*' no se pueden declarar con 'constexpr' especificador|
|C2127 de Error del compilador|'*identificador*': la inicialización no válida de entidad 'constexpr' con una expresión no constante|
|[Error del compilador C2128](compiler-error-c2128.md)|'*función*': alloc_text/same_seg solo es aplicable a funciones con vinculación C|
|[Error del compilador C2129](compiler-error-c2129.md)|función estática '*identificador*' declarada pero no definida|
|[Error del compilador C2130](compiler-error-c2130.md)|#line esperaba una cadena que contiene el nombre de archivo, se encontró '*token*'|
|C2131 de Error del compilador|expresión no evalúa como una constante|
|[Error del compilador C2132](compiler-error-c2132.md)|error de sintaxis: identificador inesperado|
|[Error del compilador C2133](compiler-error-c2133.md)|'*identificador*': tamaño desconocido|
|[Error del compilador C2134](compiler-error-c2134.md)|'*función*': llamada no da como resultado una expresión constante|
|[Error del compilador C2135](compiler-error-c2135.md)|'*operador*': operación de campo de bits no válida|
|C2136 de Error del compilador|no permitido el contrato de API de creación|
|[Error del compilador C2137](compiler-error-c2137.md)|constante de caracteres vacía|
|[Error del compilador C2138](compiler-error-c2138.md)|no es válido definir una enumeración sin miembros|
|[Error del compilador C2139](compiler-error-c2139.md)|'*clase*': no se permite una clase no definida como argumento para el rasgo de tipo intrínseco '*rasgo*'|
|[Error del compilador C2140](compiler-error-c2140.md)|'*tipo*': no se permite un tipo que depende de un parámetro de tipo genérico como un argumento para el rasgo de tipo intrínseco '*rasgo*'|
|[Error del compilador C2141](compiler-error-c2141.md)|desbordamiento del tamaño de matriz|
|[Error del compilador C2142](compiler-error-c2142.md)|las declaraciones de función son diferentes, los parámetros de variables especificados sólo en uno de ellos|
|[Error del compilador C2143](compiler-error-c2143.md)|error de sintaxis: falta '*símbolo1*'before'*token2*'|
|[Error del compilador C2144](compiler-error-c2144.md)|error de sintaxis: '*tipo*'debe ir precedido de'*token2*'|
|[Error del compilador C2145](compiler-error-c2145.md)|error de sintaxis: falta '*token*' delante del identificador|
|[Error del compilador C2146](compiler-error-c2146.md)|error de sintaxis: falta '*token*'delante del identificador'*identificador*'|
|[Error del compilador C2147](compiler-error-c2147.md)|error de sintaxis: '*token*' es una palabra clave nueva|
|[Error del compilador C2148](compiler-error-c2148.md)|tamaño total de la matriz no debe superar los 0 x*valor* bytes|
|[Error del compilador C2149](compiler-error-c2149.md)|'*identificador*': campo de bits con nombre no puede tener un ancho de cero|
|[Error del compilador C2150](compiler-error-c2150.md)|'*identificador*': campo de bits debe tener el tipo 'int', 'signed int' o 'unsigned int'|
|[Error del compilador C2151](compiler-error-c2151.md)|más de un atributo de idioma|
|[Error del compilador C2152](compiler-error-c2152.md)|'*identificador*': punteros a funciones con distintos atributos|
|[Error del compilador C2153](compiler-error-c2153.md)|los literales enteros deben tener al menos un dígito|
|[Error del compilador C2154](compiler-error-c2154.md)|'*tipo*': tipo de enumeración solo se permite como argumento para el rasgo de tipo intrínseco '*rasgo*'|
|[Error del compilador C2155](compiler-error-c2155.md)|'?': operando, se esperaba izquierdo aritméticos no válido o tipo de puntero|
|[Error del compilador C2156](compiler-error-c2156.md)|pragma debe estar fuera de la función|
|[Error del compilador C2157](compiler-error-c2157.md)|'*identificador*': se debe declarar antes de su uso en la lista pragma|
|[Error del compilador C2158](compiler-error-c2158.md)|'*tipo*': directiva #pragma make_public se admite actualmente para tipos nativos no es de plantilla solo|
|[Error del compilador C2159](compiler-error-c2159.md)|se ha especificado más de una clase de almacenamiento|
|[Error del compilador C2160](compiler-error-c2160.md)|'##' no puede aparecer al principio de una definición de macro|
|[Error del compilador C2161](compiler-error-c2161.md)|'##' no puede aparecer al final de una definición de macro|
|[Error del compilador C2162](compiler-error-c2162.md)|parámetro formal de macro esperado|
|[Error del compilador C2163](compiler-error-c2163.md)|'*función*': no disponible como función intrínseca|
|[Error del compilador C2164](compiler-error-c2164.md)|'*función*': función intrínseca no declarada|
|[Error del compilador C2165](compiler-error-c2165.md)|'*modificador*': no se puede modificar los punteros a datos|
|[Error del compilador C2166](compiler-error-c2166.md)|Valor L especifica un objeto const|
|[Error del compilador C2167](compiler-error-c2167.md)|'*función*': hay demasiados parámetros reales para la función intrínseca|
|[Error del compilador C2168](compiler-error-c2168.md)|'*función*': hay suficientes parámetros reales para la función intrínseca|
|[Error del compilador C2169](compiler-error-c2169.md)|'*función*': función intrínseca, no se puede definir|
|[Error del compilador C2170](compiler-error-c2170.md)|'*identificador*': no se ha declarado como una función, no puede ser intrínseco|
|[Error del compilador C2171](compiler-error-c2171.md)|'*operador*': no es válido para operandos de tipo '*tipo*'|
|[Error del compilador C2172](compiler-error-c2172.md)|'*función*': el parámetro real no es un puntero: parámetro *número*|
|[Error del compilador C2173](compiler-error-c2173.md)|'*función*': el parámetro real no es un puntero: parámetro *número*, lista de parámetros *número*|
|[Error del compilador C2174](compiler-error-c2174.md)|'*función*': el parámetro real es de tipo 'void': parámetro *número*, lista de parámetros *número*|
|[Error del compilador C2175](compiler-error-c2175.md)|'*configuración regional*': configuración regional no válido|
|C2176 de Error del compilador|una instrucción return no puede aparecer en el controlador de un bloque de try de función asociado a un constructor|
|[Error del compilador C2177](compiler-error-c2177.md)|constante demasiado grande|
|[Error de compilador C2178](compiler-error-c2178.md)|'*identificador*'no se pueden declarar con'*especificador*' especificador|
|[Error del compilador C2179](compiler-error-c2179.md)|'*tipo*': un argumento de atributo no puede utilizar parámetros de tipo|
|[Error del compilador C2180](compiler-error-c2180.md)|expresión de control es de tipo '*tipo*'|
|[Error del compilador C2181](compiler-error-c2181.md)|'else' no válido sin el correspondiente 'if'|
|[Error del compilador C2182](compiler-error-c2182.md)|'*identificador*': uso no válido de tipo 'void'|
|[Error del compilador C2183](compiler-error-c2183.md)|error de sintaxis: unidad de traducción está vacía|
|[Error del compilador C2184](compiler-error-c2184.md)|'*tipo*': tipo no válido para la expresión __except|
|[Error del compilador C2185](compiler-error-c2185.md)|'*identificador*': asignación con base no válida|
|[Error del compilador C2186](compiler-error-c2186.md)|'*operador*': operando no válido de tipo 'void'|
|C2187 de Error del compilador|error de sintaxis: '*token*' no se esperaba aquí|
|[Error del compilador C2188](compiler-error-c2188.md)|'*número*': demasiado grande para el carácter ancho|
|C2189 de Error del compilador|no se puede aplicar el atributo 'alignas' para un campo de bits, un parámetro de función, una declaración de excepción o una variable declarada con 'registro' clase de almacenamiento|
|[Error del compilador C2190](compiler-error-c2190.md)|primera lista de parámetros más de segundo|
|[Error del compilador C2191](compiler-error-c2191.md)|segunda lista de parámetros más larga que la primera|
|[Error del compilador C2192](compiler-error-c2192.md)|parámetro '*número*' declaración diferente|
|[Error del compilador C2193](compiler-error-c2193.md)|'*identificador*': ya se encuentran en un segmento|
|[Error del compilador C2194](compiler-error-c2194.md)|'*identificador*': es un segmento de texto|
|[Error del compilador C2195](compiler-error-c2195.md)|'*identificador*': es un segmento de datos|
|[Error del compilador C2196](compiler-error-c2196.md)|valor de Case '*valor*' ya en uso|
|[Error del compilador C2197](compiler-error-c2197.md)|'*función*': hay demasiados argumentos para la llamada|
|[Error del compilador C2198](compiler-error-c2198.md)|'*función*': hay suficientes argumentos para la llamada|
|[Error del compilador C2199](compiler-error-c2199.md)|¿error de sintaxis: se encontró '*identificador* (' en el ámbito global (era una declaración previsto)?|  