---
title: Errores del compilador de C2800 a C2899
ms.date: 04/21/2019
f1_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
helpviewer_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
ms.assetid: e5de1e92-746a-4315-a331-c5d9efb76dbb
ms.openlocfilehash: a0367d1d465d4460202f4d6d29468e59f6a74657
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856725"
---
# <a name="compiler-errors-c2800-through-c2899"></a>Errores del compilador de C2800 a C2899

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C2800](compiler-error-c2800.md)|' operador *operador*' no se puede sobrecargar|
|[Error del compilador C2801](compiler-error-c2801.md)|'*miembro*' debe ser un miembro no estático|
|[Error del compilador C2802](compiler-error-c2802.md)|miembro estático ' operator *operador*' no tiene parámetros formales|
|[Error del compilador C2803](compiler-error-c2803.md)|' operador *operador*' debe tener al menos un parámetro formal de tipo de clase|
|[Error del compilador C2804](compiler-error-c2804.md)|binario ' operador *operador*' tiene demasiados parámetros|
|[Error del compilador C2805](compiler-error-c2805.md)|binario ' operador *operador*' tiene demasiado pocos parámetros|
|[Error del compilador C2806](compiler-error-c2806.md)|' operador *operador*' tiene demasiados parámetros formales|
|[Error del compilador C2807](compiler-error-c2807.md)|el segundo parámetro formal para postfijo ' operador *operador*' debe ser 'int'|
|[Error del compilador C2808](compiler-error-c2808.md)|unario ' operador *operador*' tiene demasiados parámetros formales|
|[Error del compilador C2809](compiler-error-c2809.md)|' operador *operador*' no tiene parámetros formales|
|[Error del compilador C2810](compiler-error-c2810.md)|'*interfaz*': una interfaz solo puede heredar de otra interfaz|
|[Error del compilador C2811](compiler-error-c2811.md)|'*type1*': no puede heredar de '*type2*', una clase ref solo puede heredar de una clase ref o clase inteface|
|[Error del compilador C2812](compiler-error-c2812.md)|no se admite #import con/CLR: pure y/CLR: safe|
|[Error del compilador C2813](compiler-error-c2813.md)|No se admite #import con /MP|
|[Error del compilador C2814](compiler-error-c2814.md)|'*miembro*': un tipo nativo no puede anidarse dentro de un tipo administrado o WinRT '*clase*'|
|[Error del compilador C2815](compiler-error-c2815.md)|'operator delete': el primer parámetro formal debe ser ' void \*', pero '*tipo*' se usó|
|Error del compilador C2816|Obsoleto.|
|[Error del compilador C2817](compiler-error-c2817.md)|tipo de valor devuelto para 'operator delete' debe ser 'void'|
|[Error del compilador C2818](compiler-error-c2818.md)|aplicación de sobrecargado 'operator ->' es recursiva mediante el tipo '*clase*'|
|[Error del compilador C2819](compiler-error-c2819.md)|tipo de '*clase*' no tiene un miembro sobrecargado 'operator' ->|
|Error del compilador C2820|Obsoleto.|
|[Error del compilador C2821](compiler-error-c2821.md)|primer parámetro formal para 'operator new' debe ser 'size_t'|
|Error del compilador C2822|no se admite desenredo local en esta plataforma|
|[Error del compilador C2823](compiler-error-c2823.md)|un definición de tipo plantilla/genérico no es válido|
|[Error del compilador C2824](compiler-error-c2824.md)|tipo de valor devuelto para 'operator new' debe ser ' void \*'|
|[Error del compilador C2825](compiler-error-c2825.md)|'*identificador*': debe ser una clase o espacio de nombres cuando seguido de '::'|
|Error del compilador C2826|Obsoleto.|
|[Error del compilador C2827](compiler-error-c2827.md)|' operador *operador*' no se puede invalidar globalmente por un tipo unario|
|[Error del compilador C2828](compiler-error-c2828.md)|' operador *operador*' no se puede invalidar globalmente por un tipo binario|
|[Error del compilador C2829](compiler-error-c2829.md)|' operador *operador*' no puede tener una lista de parámetros variable|
|[Error del compilador C2830](compiler-error-c2830.md)|solo los parámetros de ubicación para 'operator new' pueden tener valores predeterminados|
|[Error del compilador C2831](compiler-error-c2831.md)|' operador *operador*' no puede tener parámetros predeterminados|
|Error del compilador C2832|'*identificador*': un tipo de referencia no puede ser el valor inicializado|
|[Error del compilador C2833](compiler-error-c2833.md)|' operador *token*' no es un operador o tipo reconocido|
|[Error del compilador C2834](compiler-error-c2834.md)|' operador *operador*' debe calificar globalmente|
|[Error del compilador C2835](compiler-error-c2835.md)|conversión definida por el usuario '*tipo*' no adopta parámetros formales|
|Error del compilador C2836|'*identificador*': miembro de datos no estáticos solo de una unión puede tener un inicializador de miembro predeterminado|
|Error del compilador C2837|'*función*': no se puede usar directivas de OpenMP y #pragma Loop (hint_parallel) en la misma función|
|[Error del compilador C2838](compiler-error-c2838.md)|'*identificador*': nombre completo no válido en la declaración de miembro|
|[Error del compilador C2839](compiler-error-c2839.md)|tipo de valor devuelto no válido '*tipo*' para sobrecargado 'operator ->'|
|Error del compilador C2840|argumento de palabra de instrucción máquina no constante|
|Error del compilador C2841|registrar el argumento no constante|
|[Error del compilador C2842](compiler-error-c2842.md)|'*clase*': un tipo administrado o WinRT no puede definir su propio 'operator new' u 'operator delete'|
|[Error del compilador C2843](compiler-error-c2843.md)|'*miembro*': no se puede adquirir la dirección de un miembro de datos no estáticos o método de un tipo administrado o WinRT|
|[Error del compilador C2844](compiler-error-c2844.md)|'*identificador*': no puede ser un miembro de interfaz '*interfaz*'|
|[Error del compilador C2845](compiler-error-c2845.md)|'*tipo*': no se permite en este tipo de aritmética de puntero|
|[Error del compilador C2846](compiler-error-c2846.md)|'*interfaz*': una interfaz no puede tener un constructor|
|[Error del compilador C2847](compiler-error-c2847.md)|no se puede aplicar sizeof al tipo administrado o WinRT '*clase*'|
|Error del compilador C2848|'*clase*': un tipo administrado o WinRT no puede ser un miembro de una unión|
|[Error del compilador C2849](compiler-error-c2849.md)|'*interfaz*': una interfaz no puede tener un destructor|
|[Error del compilador C2850](compiler-error-c2850.md)|'*construir*': solo se permite en el ámbito de archivo; no puede estar en una construcción anidada|
|Error del compilador C2851|'*enum*': Una enumeración de WinRT pública solo puede usar 'int' o 'unsigned int' como tipo base|
|Error del compilador C2852|'*identificador*': solo los miembros de datos se pueden inicializar dentro de una clase|
|Error del compilador C2853|'*identificador*': un miembro de datos no estático no puede tener un tipo que contiene 'auto'|
|[Error del compilador C2854](compiler-error-c2854.md)|error de sintaxis en #pragma hdrstop|
|[Error del compilador C2855](compiler-error-c2855.md)|opción de línea de comandos '*opción*' incoherente con el encabezado precompilado|
|[Error del compilador C2856](compiler-error-c2856.md)|#pragma hdrstop no puede estar dentro de un bloque #if|
|[Error del compilador C2857](compiler-error-c2857.md)|' #include ' instrucción especificada con la/Yc*filename* no se encontró la opción de línea de comandos en el archivo de origen|
|[Error del compilador C2858](compiler-error-c2858.md)|opción de línea de comandos ' / Yc (/Fd*filename*)' incoherente con el encabezado precompilado, que utilizó ' /Fd*filename*'|
|[Error del compilador C2859](compiler-error-c2859.md)|*nombre de archivo* no es el *filetype* archivo que se usó cuando creó este encabezado precompilado, vuelva a crear el encabezado precompilado.|
|[Error del compilador C2860](compiler-error-c2860.md)|'void' no puede ser un tipo de argumento, excepto '(void)'|
|[Error del compilador C2861](compiler-error-c2861.md)|'*declaración*': no se puede definir una función miembro de interfaz|
|[Error del compilador C2862](compiler-error-c2862.md)|'*interfaz*': una interfaz solo puede tener miembros públicos|
|[Error del compilador C2863](compiler-error-c2863.md)|'*interfaz*': una interfaz no puede tener elementos Friend|
|[Error del compilador C2864](compiler-error-c2864.md)|'*identificador*': una variable de miembro o una plantilla de datos estáticos con un inicializador in-class debe tener un tipo integral const no volátil|
|[Error del compilador C2865](compiler-error-c2865.md)|'*operador*': comparación no válida de puntero o identificador de objeto|
|Error del compilador C2866|Obsoleto.|
|[Error del compilador C2867](compiler-error-c2867.md)|'*identificador*': no es un espacio de nombres|
|[Error del compilador C2868](compiler-error-c2868.md)|'*identificador*': sintaxis no válida para la declaración using; esperado nombre completo|
|[Error del compilador C2869](compiler-error-c2869.md)|'*identificador*': ya se ha definido para que sea un espacio de nombres|
|[Error del compilador C2870](compiler-error-c2870.md)|'*identificador*': una definición de espacio de nombres debe aparecer en el ámbito de archivo o directamente dentro de otra definición de espacio de nombres|
|[Error del compilador C2871](compiler-error-c2871.md)|'*identificador*': no existe un espacio de nombres con este nombre|
|[Error del compilador C2872](compiler-error-c2872.md)|'*identificador*': símbolo ambiguo|
|[Error del compilador C2873](compiler-error-c2873.md)|'*símbolo*': símbolo no se puede usar en una declaración using|
|[Error del compilador C2874](compiler-error-c2874.md)|la declaración using crea una declaración múltiple de '*identificador*'|
|[Error del compilador C2875](compiler-error-c2875.md)|la declaración using crea una declaración múltiple de '*clase*::*identificador*'|
|[Error del compilador C2876](compiler-error-c2876.md)|'*clase*::*miembro*': no todas las sobrecargas son accesibles|
|[Error del compilador C2877](compiler-error-c2877.md)|'*miembro*'no es accesible desde'*clase*'|
|[Error del compilador C2878](compiler-error-c2878.md)|'*identificador*': no existe un espacio de nombres o clase de este nombre|
|[Error del compilador C2879](compiler-error-c2879.md)|'*identificador*': sólo un espacio de nombres existente se puede proporcionar un nombre alternativo mediante una definición de alias de espacio de nombres|
|Error del compilador C2880|__swi o __hvc requiere una constante válida como primer argumento (número SWI)|
|[Error del compilador C2881](compiler-error-c2881.md)|'*identificador*': ya se utiliza como un alias para '*clase*'|
|[Error del compilador C2882](compiler-error-c2882.md)|'*identificador*': uso no válido de identificador de espacio de nombres en la expresión|
|[Error del compilador C2883](compiler-error-c2883.md)|'*función*': declaración de función entra en conflicto con '*identificador*' introducidos por la declaración using|
|[Error del compilador C2884](compiler-error-c2884.md)|'*identificador*': introducido por la declaración using entra en conflicto con la función local '*función*'|
|[Error del compilador C2885](compiler-error-c2885.md)|'*clase*::*identificador*': no es una declaración using válida en el ámbito de no clase|
|[Error del compilador C2886](compiler-error-c2886.md)|'*clase*::*identificador*': símbolo no se puede usar en una declaración using de miembro|
|Error del compilador C2887|__swi o __hvc no puede tener más de cinco argumentos (número SWI, r0 - r3)|
|[Error del compilador C2888](compiler-error-c2888.md)|'*identificador*': símbolo no se pueden definir dentro del espacio de nombres '*espacio de nombres*'|
|Error del compilador C2889|'*clase*': un tipo de clase administrada o WinRT no puede ser una clase base virtual|
|[Error del compilador C2890](compiler-error-c2890.md)|'*clase*': una clase ref solo puede tener una clase base sin interfaz|
|[Error del compilador C2891](compiler-error-c2891.md)|'*parámetro*': no se puede adquirir la dirección de un parámetro de plantilla|
|[Error del compilador C2892](compiler-error-c2892.md)|clase local no debe tener plantillas de miembro|
|[Error del compilador C2893](compiler-error-c2893.md)|No se pudo especializar la plantilla de función '*plantilla*'|
|[Error del compilador C2894](compiler-error-c2894.md)|las plantillas no se pueden declarar tenga vinculación 'C'|
|Error del compilador C2895|'*declaración*': no se puede crear explícitamente instancias de una plantilla de función que se ha declarado con dllimport|
|[Error del compilador C2896](compiler-error-c2896.md)|'*función1*': no se puede usar la función de plantilla o genérico '*función2*' como argumento de función|
|[Error del compilador C2897](compiler-error-c2897.md)|un destructor/finalizador no puede ser una plantilla de función|
|[Error del compilador C2898](compiler-error-c2898.md)|'*declaración*': las plantillas de función miembro no pueden ser virtuales|
|Error del compilador C2899|Obsoleto.|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
