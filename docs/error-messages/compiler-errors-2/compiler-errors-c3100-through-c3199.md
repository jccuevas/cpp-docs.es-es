---
title: Errores del compilador de C3100 a C3199
ms.date: 04/21/2019
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
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
ms.openlocfilehash: efa3207a9fdfb81a52bf319a1cbc2da84084b6cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281660"
---
# <a name="compiler-errors-c3100-through-c3199"></a>Errores del compilador de C3100 a C3199

Los artículos de esta sección de la documentación explican un subconjunto de los mensajes de error generados por el compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensajes de error

|Error|Mensaje|
|-----------|-------------|
|[Error del compilador C3100](compiler-error-c3100.md)|'*identificador*': calificador de atributo desconocido|
|[Error del compilador C3101](compiler-error-c3101.md)|expresión no válida para el argumento de atributo con nombre '*identificador*'|
|Error del compilador C3102|Obsoleto.|
|[Error del compilador C3103](compiler-error-c3103.md)|'*identificador*': argumento con nombre repetido|
|[Error del compilador C3104](compiler-error-c3104.md)|argumento de atributo no válido|
|Error del compilador C3105|'*símbolo*': no se puede usar como un atributo|
|[Error del compilador C3106](compiler-error-c3106.md)|'*atributo*': los argumentos sin nombre deben preceder a los argumentos con nombre|
|Error del compilador C3107|'*atributo*': no se pueden definir funciones miembro de atributos nativos|
|Error del compilador C3108|no se puede deducir un tipo como una lista de inicializadores no es una expresión|
|Error del compilador C3109|'*identificador*': deben usar los métodos de interfaz '__stdcall' o '__cdecl' convención de llamada|
|[Error del compilador C3110](compiler-error-c3110.md)|'*función*': no se pueden sobrecargar un método de interfaz COM|
|Error del compilador C3111|No se puede usar una lista de inicializadores como argumento predeterminado para un parámetro de plantilla|
|Error del compilador C3112|'*interfaz*': una interfaz solo puede declararse en global o ámbito de espacio de nombres|
|[Error del compilador C3113](compiler-error-c3113.md)|una "interfaz o enumeración' no puede ser un plantilla o genérico|
|[Error del compilador C3114](compiler-error-c3114.md)|'*identificador*': argumento de atributo no válido con nombre|
|[Error del compilador C3115](compiler-error-c3115.md)|'*atributo*': este atributo no se permite en '*construir*'|
|[Error del compilador C3116](compiler-error-c3116.md)|'*especificador*': clase de almacenamiento no es válida para el método de interfaz|
|[Error del compilador C3117](compiler-error-c3117.md)|'*interfaz*': una interfaz solo puede tener una clase base|
|[Error del compilador C3118](compiler-error-c3118.md)|'*interfaz*': las interfaces no admiten la herencia virtual|
|Error del compilador C3119|no se permite alignas (void)|
|[Error del compilador C3120](compiler-error-c3120.md)|'*identificador*': los métodos de interfaz no pueden tomar una lista de argumentos variables|
|[Error del compilador C3121](compiler-error-c3121.md)|no se puede cambiar el GUID para la clase*clase*'|
|Error del compilador C3122|'*interfaz*': una interfaz genérica de WinRT no puede tener GUID|
|Error del compilador C3123|Interfaz genérica de WinRT no puede tener restricciones|
|Error del compilador C3124|'signed char' no es un tipo de datos válido de WinRT. Use 'unsigned char', 'wchar_t' o 'signed short' en su lugar.|
|Error del compilador C3125|'*tipo*': tipo no se puede derivar, directa o indirectamente de 'Platform:: Exception'|
|[Error del compilador C3126](compiler-error-c3126.md)|no se puede definir una unión '*unión*'dentro del tipo administrado o WinRT'*tipo*'|
|Error del compilador C3127|'*tipo*': '*rasgo*' rasgo solo puede usarse en una clase ref de WinRT|
|Error del compilador C3128|'*tipo*'no tiene un objeto vtable especificado por'*tipo*'|
|Error del compilador C3129|'*tipo*': __default_vptr_for_base solo se puede usar en bases y tipos polimórficos definidos localmente|
|[Error del compilador C3130](compiler-error-c3130.md)|Error interno del compilador: no se pudo escribir el bloque de código insertado en PDB|
|[Error del compilador C3131](compiler-error-c3131.md)|proyecto debe tener un atributo 'module' con una propiedad 'name'|
|[Error del compilador C3132](compiler-error-c3132.md)|'*parámetro*': las matrices de parámetros solo se pueden aplicar a un argumento formal de tipo 'matriz unidimensional de administrada o WinRT'|
|[Error del compilador C3133](compiler-error-c3133.md)|No se puede aplicar atributos a varargs de C++|
|[Error del compilador C3134](compiler-error-c3134.md)|'*valor*': el valor del argumento del atributo '*argumento*'no tiene tipo válido de'*tipo*'|
|[Error del compilador C3135](compiler-error-c3135.md)|'*identificador*': una propiedad no puede tener 'const' o 'volatile' de tipo|
|[Error del compilador C3136](compiler-error-c3136.md)|'*interfaz*': una interfaz COM solo puede heredar de otra interfaz COM, '*interfaz*' no es una interfaz COM|
|[Error del compilador C3137](compiler-error-c3137.md)|'*identificador*': no se puede inicializar una propiedad|
|[Error del compilador C3138](compiler-error-c3138.md)|'*identificador*': un '*atributo*' interfaz debe heredar de IDispatch o de una interfaz que hereda de IDispatch|
|[Error del compilador C3139](compiler-error-c3139.md)|'*tipo*': no se puede exportar un tipo definido por el usuario sin miembros|
|[Error del compilador C3140](compiler-error-c3140.md)|no puede tener varios atributos 'module' en la misma unidad de compilación|
|[Error del compilador C3141](compiler-error-c3141.md)|'*interfaz*': las interfaces solo admiten herencia pública|
|[Error del compilador C3142](compiler-error-c3142.md)|'*propiedad*': no puede tomar la dirección de una propiedad|
|Error del compilador C3143|'*argumento*': argumento de atributo no puede tener varios valores|
|Error del compilador C3144|'*atributo*': atributo requiere argumentos explícitos, '*argumento*' no tiene nombre|
|[Error del compilador C3145](compiler-error-c3145.md)|'*identificador*': variable global o estática no puede tener el tipo administrado o WinRT '*tipo*'|
|Error del compilador C3146|Obsoleto.|
|Error del compilador al error C3147|Obsoleto.|
|Error del compilador C3148|Obsoleto.|
|[Error del compilador C3149](compiler-error-c3149.md)|'*tipo*': no se puede usar este tipo aquí sin un nivel superior '*token*'|
|[Error del compilador C3150](compiler-error-c3150.md)|'*construir*': '*atributo*' sólo puede aplicarse a una clase, struct, interfaz, matriz o puntero|
|Error del compilador C3151|Obsoleto.|
|[Error del compilador C3152](compiler-error-c3152.md)|'*función*': '*palabra clave*' sólo puede aplicarse a una clase, struct o función miembro virtual|
|[Error del compilador C3153](compiler-error-c3153.md)|'*interfaz*': no se puede crear una instancia de una interfaz|
|[Error del compilador C3154](compiler-error-c3154.md)|Se esperaba ',' antes de puntos suspensivos. No coma separada por puntos suspensivos no compatible con funciones de matriz.|
|[Error del compilador C3155](compiler-error-c3155.md)|no se permiten atributos en un indizador de propiedad|
|[Error del compilador C3156](compiler-error-c3156.md)|'*clase*': no puede tener una definición local de un tipo administrado o WinRT|
|[Error del compilador C3157](compiler-error-c3157.md)|Atributo ParamArray solamente se puede aplicar al último parámetro|
|Error del compilador C3158|'*función*': '*palabra clave*' solo puede aplicarse a una función miembro virtual|
|[Error del compilador C3159](compiler-error-c3159.md)|'*identificador*': no se puede declarar la matriz de punteros a tipo de valor|
|[Error del compilador C3160](compiler-error-c3160.md)|'*tipo*': un miembro de datos de una clase administrada o WinRT no puede tener este tipo|
|[Error del compilador C3161](compiler-error-c3161.md)|'*interfaz*': anidamiento class, struct o interfaz en una interfaz no es válido; el anidamiento de una interfaz en una clase o struct no es válido|
|[Error del compilador C3162](compiler-error-c3162.md)|'*tipo*': un tipo de referencia que tiene un destructor no se puede usar como el tipo de miembro de datos estático '*miembro*'|
|[Error del compilador C3163](compiler-error-c3163.md)|'*clase*': atributos incoherentes con la declaración anterior|
|Error del compilador C3164|Obsoleto.|
|Error del compilador C3165|'*valor*': no se puede convertir en un valor integral o de punto flotante|
|[Error del compilador C3166](compiler-error-c3166.md)|Obsoleto. '*tipo*': un miembro de datos de una clase administrada o WinRT no puede tener el tipo '*tipo_de_puntero* interiores a *managed_pointer_type*'|
|[Error del compilador C3167](compiler-error-c3167.md)|No se puede inicializar .NET Framework: asegúrese de que está instalado|
|[Error del compilador C3168](compiler-error-c3168.md)|'*tipo*': tipo de enumeración subyacente no válido|
|Error del compilador C3169|'*tipo*': no se puede deducir el tipo de 'auto' desde '*tipo*'|
|[Error del compilador C3170](compiler-error-c3170.md)|no puede tener identificadores de módulo distintos en un proyecto|
|[Error del compilador C3171](compiler-error-c3171.md)|'*módulo*': no se puede especificar atributos module distintos en un proyecto|
|[Error del compilador C3172](compiler-error-c3172.md)|'*identificador*': no se puede especificar distintos atributos idl_module en un proyecto|
|[Error del compilador C3173](compiler-error-c3173.md)|Error de coincidencia de versión en la combinación de idl|
|[Error del compilador C3174](compiler-error-c3174.md)|no se especificó el atributo de módulo|
|[Error del compilador C3175](compiler-error-c3175.md)|'*función*': no se puede llamar a un método de un tipo administrado desde la función no administrada '*función*'|
|[Error del compilador C3176](compiler-error-c3176.md)|'*tipo*': no se puede declarar el tipo de valor local|
|Error del compilador C3177|no puede tener una función de conversión a un tipo que contiene '*tipo*'|
|Error del compilador C3178|'*tipo*': no se puede utilizar ParamArray en una función con argumentos predeterminados|
|[Error del compilador C3179](compiler-error-c3179.md)|no se permite un tipo administrado o WinRT sin nombre|
|[Error del compilador C3180](compiler-error-c3180.md)|'*tipo*': nombre supera el límite de metadatos de '*número*' caracteres|
|[Error del compilador C3181](compiler-error-c3181.md)|'*tipo*': operando no válido para *operador*|
|[Error del compilador C3182](compiler-error-c3182.md)|'*tipo*': una declaración de acceso o la declaración using de miembro no es válida dentro de un tipo administrado o WinRT|
|[Error del compilador C3183](compiler-error-c3183.md)|no se puede definir sin nombre de clase, struct o union dentro del tipo administrado o WinRT '*clase*'|
|Error del compilador C3184|Obsoleto.|
|[Error del compilador error C3185](compiler-error-c3185.md)|'typeid': utilizado en el tipo administrado o WinRT '*tipo*', utilice '*operador*' en su lugar|
|Error del compilador C3186|Obsoleto.|
|[Error del compilador C3187](compiler-error-c3187.md)|'*identificador*': solo está disponible dentro del cuerpo de una función|
|Error del compilador C3188|Obsoleto.|
|[Error del compilador C3189](compiler-error-c3189.md)|' typeid <*declarador*>': esta sintaxis ya no es compatible, utilice:: typeid en su lugar|
|[Error del compilador C3190](compiler-error-c3190.md)|'*declarador*'con los argumentos de plantilla proporcionado no es la creación de instancias explícita de ninguna función miembro de'*tipo*'|
|Error del compilador C3191|Obsoleto.|
|[Error del compilador C3192](compiler-error-c3192.md)|error de sintaxis: ' ^' no es un operador de prefijo (¿pretendía utilizar ' *'?)|
|Error del compilador C3193|'*construir*': requiere ' / clr' o ' / ZW' opción de línea de comandos|
|[Error del compilador C3194](compiler-error-c3194.md)|'*tipo*': un tipo de valor no puede tener un operador de asignación|
|[Error del compilador C3195](compiler-error-c3195.md)|'*palabra clave*': está reservado y no se puede usar como un miembro de un tipo de valor o clase ref. Los operadores CLR o WinRT deben definirse mediante la palabra clave 'operator'|
|[Error del compilador C3196](compiler-error-c3196.md)|'*identificador*': puede usar más de una vez|
|[Error del compilador C3197](compiler-error-c3197.md)|'*palabra clave*': solamente se puede utilizar en definiciones|
|[Error del compilador C3198](compiler-error-c3198.md)|uso no válido de pragmas de punto flotante: el pragma fenv_access solamente funciona en el modo preciso|
|[Error del compilador C3199](compiler-error-c3199.md)|uso no válido de pragmas de punto flotante: no se admiten excepciones en el modo no preciso|

## <a name="see-also"></a>Vea también

[C /C++ herramientas errores y advertencias de compilación y el compilador](../compiler-errors-1/c-cpp-build-errors.md) \
[Errores del compilador de C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
