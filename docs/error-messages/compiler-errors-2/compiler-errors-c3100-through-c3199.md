---
title: C3100 de errores del compilador a través de C3199 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
helpviewer_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
dev_langs:
- C++
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 062ab968a51c38e9418a96b0df07eec3ae399ac3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283899"
---
# <a name="compiler-errors-c3100-through-c3199"></a>C3100 de errores del compilador a través de C3199

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C3100](compiler-error-c3100.md)|'*identificador*': calificador de atributo desconocido|
|[Error del compilador C3101](compiler-error-c3101.md)|expresión no válida para el argumento de atributo con nombre '*identificador*'|
|C3102 de Error del compilador|Obsoleto.|
|[Error del compilador C3103](compiler-error-c3103.md)|'*identificador*': argumento con nombre repetido|
|[Error del compilador C3104](compiler-error-c3104.md)|argumento de atributo no válido|
|C3105 de Error del compilador|'*símbolo*': no se puede usar como un atributo|
|[Error del compilador C3106](compiler-error-c3106.md)|'*atributo*': los argumentos sin nombre deben preceder a los argumentos con nombre|
|C3107 de Error del compilador|'*atributo*': no se pueden definir funciones de miembro de atributos nativos|
|C3108 de Error del compilador|no se puede deducir un tipo como una lista de inicializador no es una expresión|
|C3109 de Error del compilador|'*identificador*': métodos de interfaz deben utilizar el '__stdcall' o '__cdecl' convención de llamada|
|[Error del compilador C3110](compiler-error-c3110.md)|'*función*': no se pueden sobrecargar un método de interfaz com.|
|C3111 de Error del compilador|No se puede usar una lista de inicializadores como el argumento predeterminado para un parámetro de plantilla|
|C3112 de Error del compilador|'*interfaz*': una interfaz solo puede declararse en global o en el ámbito de espacio de nombres|
|[Error del compilador C3113](compiler-error-c3113.md)|una 'interfaz o enumeración' no puede ser una plantilla/generic|
|[Error del compilador C3114](compiler-error-c3114.md)|'*identificador*': argumento de atributo no válido con nombre|
|[Error del compilador C3115](compiler-error-c3115.md)|'*atributo*': este atributo no se permite en '*construir*'|
|[Error del compilador C3116](compiler-error-c3116.md)|'*especificador*': clase de almacenamiento no es válida para el método de interfaz|
|[Error del compilador C3117](compiler-error-c3117.md)|'*interfaz*': una interfaz solo puede tener una clase base|
|[Error del compilador C3118](compiler-error-c3118.md)|'*interfaz*': las interfaces no admiten herencia virtual|
|C3119 de Error del compilador|no se permite alignas(void)|
|[Error del compilador C3120](compiler-error-c3120.md)|'*identificador*': métodos de interfaz no pueden tomar una lista de argumentos variables|
|[Error del compilador C3121](compiler-error-c3121.md)|no se puede cambiar el GUID para la clase*clase*'|
|C3122 de Error del compilador|'*interfaz*': una interfaz genérica de WinRT no puede tener GUID|
|C3123 de Error del compilador|Interfaz genérica de WinRT no puede tener restricciones|
|C3124 de Error del compilador|'signed char' no es un tipo de datos de WinRT válido. Use 'unsigned char', 'wchar_t' o 'signed short' en su lugar.|
|C3125 de Error del compilador|'*tipo*': tipo no puede derivar directa o indirectamente de 'Exception'|
|[Error del compilador C3126](compiler-error-c3126.md)|no se puede definir una unión '*union*'dentro del tipo administrado o WinRT'*tipo*'|
|C3127 de Error del compilador|'*tipo*': '*rasgo*' rasgo solo puede usarse en una clase ref de WinRT|
|C3128 de Error del compilador|'*tipo*'no tiene una tabla virtual que se introdujo por'*tipo*'|
|C3129 de Error del compilador|'*tipo*': __default_vptr_for_base sólo puede utilizarse en tipos polimórficos definidos localmente y bases de datos|
|[Error del compilador C3130](compiler-error-c3130.md)|Error interno del compilador: no se pudo escribir el bloque de código insertado en PDB|
|[Error del compilador C3131](compiler-error-c3131.md)|proyecto debe tener un atributo 'module' con una propiedad 'name'|
|[Error del compilador C3132](compiler-error-c3132.md)|'*parámetro*': las matrices de parámetros solo pueden aplicarse a un argumento formal del tipo 'matriz unidimensional de administrado o WinRT'|
|[Error del compilador C3133](compiler-error-c3133.md)|No se pueden aplicar atributos a varargs de C++|
|[Error del compilador C3134](compiler-error-c3134.md)|'*valor*': valor de argumento de atributo '*argumento*'no tiene tipo válido de'*tipo*'|
|[Error del compilador C3135](compiler-error-c3135.md)|'*identificador*': una propiedad no puede tener 'const' o 'volatile' Escriba|
|[Error del compilador C3136](compiler-error-c3136.md)|'*interfaz*': una interfaz COM sólo puede heredar de otra interfaz COM, '*interfaz*' no es una interfaz COM|
|[Error del compilador C3137](compiler-error-c3137.md)|'*identificador*': no se puede inicializar una propiedad|
|[Error del compilador C3138](compiler-error-c3138.md)|'*identificador*': un '*atributo*' interfaz debe heredar de IDispatch o de una interfaz que hereda de IDispatch|
|[Error del compilador C3139](compiler-error-c3139.md)|'*tipo*': no se puede exportar un tipo definido por el usuario sin miembros|
|[Error del compilador C3140](compiler-error-c3140.md)|no puede tener varios atributos 'module' en la misma unidad de compilación|
|[Error del compilador C3141](compiler-error-c3141.md)|'*interfaz*': interfaces sólo admiten herencia pública|
|[Error del compilador C3142](compiler-error-c3142.md)|'*propiedad*': no se puede adquirir la dirección de una propiedad|
|C3143 de Error del compilador|'*argumento*': argumento de atributo no puede tener varios valores|
|C3144 de Error del compilador|'*atributo*': atributo requiere argumentos explícitos, '*argumento*' no tiene nombre|
|[Error del compilador C3145](compiler-error-c3145.md)|'*identificador*': la variable global o estática no puede tener el tipo administrado o WinRT '*tipo*'|
|C3146 de Error del compilador|Obsoleto.|
|Error de compilador al error C3147|Obsoleto.|
|C3148 de Error del compilador|Obsoleto.|
|[Error del compilador C3149](compiler-error-c3149.md)|'*tipo*': no se puede usar este tipo aquí sin un nivel superior '*token*'|
|[Error del compilador C3150](compiler-error-c3150.md)|'*construir*': '*atributo*' solo se puede aplicar a una clase, estructura, interfaz, matriz o puntero|
|C3151 de Error del compilador|Obsoleto.|
|[Error del compilador C3152](compiler-error-c3152.md)|'*función*': '*palabra clave*' solo se puede aplicar a una clase, struct o función miembro virtual|
|[Error del compilador C3153](compiler-error-c3153.md)|'*interfaz*': no se puede crear una instancia de una interfaz|
|[Error del compilador C3154](compiler-error-c3154.md)|Se esperaba ',' antes de puntos suspensivos. No coma separada puntos suspensivos que no se admiten en las funciones de matriz de parámetros.|
|[Error del compilador C3155](compiler-error-c3155.md)|no se permiten atributos en una propiedad de indizador|
|[Error del compilador C3156](compiler-error-c3156.md)|'*clase*': no se puede tener una definición local de un tipo administrado o WinRT|
|[Error del compilador C3157](compiler-error-c3157.md)|Atributo de ParamArray sólo se puede aplicar al último parámetro|
|C3158 de Error del compilador|'*función*': '*palabra clave*' solo se puede aplicar a una función miembro virtual|
|[Error del compilador C3159](compiler-error-c3159.md)|'*identificador*': no se puede declarar la matriz de punteros a tipo de valor|
|[Error del compilador C3160](compiler-error-c3160.md)|'*tipo*': un miembro de datos de una clase administrada o WinRT no puede tener este tipo|
|[Error del compilador C3161](compiler-error-c3161.md)|'*interfaz*': anidamiento class, struct o interfaz en una interfaz no es válido; el anidamiento de una interfaz en una clase o struct no es válido|
|[Error del compilador C3162](compiler-error-c3162.md)|'*tipo*': un tipo de referencia que tiene un destructor no se puede usar como el tipo de miembro de datos estático '*miembro*'|
|[Error del compilador C3163](compiler-error-c3163.md)|'*clase*': atributos incoherentes con la declaración anterior.|
|C3164 de Error del compilador|Obsoleto.|
|C3165 de Error del compilador|'*valor*': no se puede convertir en un valor entero o de punto flotante|
|[Error del compilador C3166](compiler-error-c3166.md)|Obsoleto. '*tipo*': un miembro de datos de una clase administrada o WinRT no puede tener el tipo '*tipo_de_puntero* interior a *managed_pointer_type*'|
|[Error del compilador C3167](compiler-error-c3167.md)|No se puede inicializar .NET Framework: asegúrese de que está instalado|
|[Error del compilador C3168](compiler-error-c3168.md)|'*tipo*': tipo de enumeración subyacente no válido|
|C3169 de Error del compilador|'*tipo*': no se puede deducir el tipo de 'auto' de '*tipo*'|
|[Error del compilador C3170](compiler-error-c3170.md)|no pueden tener identificadores de módulo distintos en un proyecto|
|[Error del compilador C3171](compiler-error-c3171.md)|'*módulo*': no se puede especificar atributos module distintos en un proyecto|
|[Error del compilador C3172](compiler-error-c3172.md)|'*identificador*': no se puede especificar distintos atributos idl_module en un proyecto|
|[Error del compilador C3173](compiler-error-c3173.md)|Error de coincidencia de versión en la combinación de idl|
|[Error del compilador C3174](compiler-error-c3174.md)|no se especificó el atributo de módulo|
|[Error del compilador C3175](compiler-error-c3175.md)|'*función*': no se puede llamar a un método de un tipo administrado desde la función no administrada '*función*'|
|[Error del compilador C3176](compiler-error-c3176.md)|'*tipo*': no se puede declarar el tipo de valor local|
|C3177 de Error del compilador|no puede tener una función de conversión a un tipo que contiene '*tipo*'|
|C3178 de Error del compilador|'*tipo*': no se puede usar ParamArray en una función con argumentos predeterminados|
|[Error del compilador C3179](compiler-error-c3179.md)|no se permite un tipo administrado o WinRT sin nombre|
|[Error del compilador C3180](compiler-error-c3180.md)|'*tipo*': nombre supera el límite de metadatos de '*número*' caracteres|
|[Error del compilador C3181](compiler-error-c3181.md)|'*tipo*': operando no válido para *(operador)*|
|[Error del compilador C3182](compiler-error-c3182.md)|'*tipo*': una declaración de acceso o declaración using de miembro no es válida dentro de un tipo administrado o WinRT|
|[Error del compilador C3183](compiler-error-c3183.md)|no se puede definir sin nombre de clase, struct o union dentro del tipo administrado o WinRT '*clase*'|
|C3184 de Error del compilador|Obsoleto.|
|[Error del compilador C3185](compiler-error-c3185.md)|'typeid': utilizado en el tipo administrado o WinRT '*tipo*', use '*operador*' en su lugar|
|Error del compilador C3186|Obsoleto.|
|[Error del compilador C3187](compiler-error-c3187.md)|'*identificador*': solamente está disponible en el cuerpo de una función|
|C3188 de Error del compilador|Obsoleto.|
|[Error del compilador C3189](compiler-error-c3189.md)|' typeid <*declarador*>': esta sintaxis ya no es compatible, use::typeid en su lugar|
|[Error del compilador C3190](compiler-error-c3190.md)|'*declarador*'con los argumentos de plantilla proporcionados no es la creación de instancias explícita de ninguna función miembro de'*tipo*'|
|C3191 de Error del compilador|Obsoleto.|
|[Error del compilador C3192](compiler-error-c3192.md)|error de sintaxis: ' ^' no es un operador de prefijo (¿quiso decir ' *'?)|
|C3193 de Error del compilador|'*construir*': requiere ' / clr' o ' / ZW' opción de línea de comandos|
|[Error del compilador C3194](compiler-error-c3194.md)|'*tipo*': un tipo de valor no puede tener un operador de asignación|
|[Error del compilador C3195](compiler-error-c3195.md)|'*palabra clave*': está reservado y no se puede usar como un miembro de un tipo de valor o clase ref. Operadores CLR o WinRT se deben definir mediante la palabra clave 'operator'|
|[Error del compilador C3196](compiler-error-c3196.md)|'*identificador*': utilizado más de una vez|
|[Error del compilador C3197](compiler-error-c3197.md)|'*palabra clave*': solo puede usarse en definiciones|
|[Error del compilador C3198](compiler-error-c3198.md)|uso no válido de pragmas de punto flotante: fenv_access (pragma) funciona solo en el modo preciso|
|[Error del compilador C3199](compiler-error-c3199.md)|uso no válido de pragmas de punto flotante: excepciones no se admiten en el modo no es preciso|
