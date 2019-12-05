---
title: Tipos fundamentales (C++)
ms.date: 11/04/2016
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: daa2ad2680a9d7d0239a70ed37ec1d90a3d96d97
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857546"
---
# <a name="fundamental-types--c"></a>Tipos fundamentales (C++)

Los tipos fundamentales de C++ se dividen en tres categorías: entero, punto flotante y void. Los tipos enteros son capaces de controlar números enteros. Los tipos de punto flotante son capaces de especificar valores que pueden tener partes fraccionarias.

El tipo [void](../cpp/void-cpp.md) describe un conjunto de valores vacío. No se puede especificar ninguna variable de tipo **void** : se utiliza principalmente para declarar funciones que no devuelven valores o para declarar punteros genéricos a datos sin tipo o con tipo arbitrario. Cualquier expresión se puede convertir o convertir explícitamente al tipo **void**. Sin embargo, estas expresiones se limitan a los siguientes usos:

- Una instrucción de expresión. (Vea [Expresiones](../cpp/expressions-cpp.md)para obtener más información).

- El operando izquierdo del operador de coma. (Vea [Operador de coma](../cpp/comma-operator.md) para obtener más información).

- El segundo o tercer operando del operador condicional (`? :`). (Vea [Expresiones con el operador condicional](../cpp/conditional-operator-q.md) para obtener más información).

En la tabla siguiente se explican las restricciones en los tamaños de tipo. Estas restricciones son independientes de la implementación de Microsoft.

### <a name="fundamental-types-of-the-c-language"></a>Tipos fundamentales del lenguaje C++

|Categoría|Tipo de|Contenido|
|--------------|----------|--------------|
|Entero|**char**|Tipo **Char** es un tipo entero que normalmente contiene miembros del juego de caracteres de ejecución básico; de forma predeterminada, es ASCII en C++Microsoft.<br /><br /> El C++ compilador trata las variables de tipo **Char**, **signed char**y **unsigned char** como si tuvieran tipos diferentes. Las variables de tipo **Char** se promueven a **int** como si fueran de tipo **signed char** de forma predeterminada, a menos que se use la opción de compilación/j. En este caso, se tratan como tipo **unsigned char** y se promueven a **int** sin la extensión de signo.|
||**bool**|El tipo **bool** es un tipo entero que puede tener uno de los dos valores **true** o **false**. Su tamaño no está especificado.|
||**short**|El tipo **Short int** (o simplemente **Short**) es un tipo entero que es mayor o igual que el tamaño del tipo **Char**y menor o igual que el tamaño del tipo **int**.<br /><br /> Los objetos de tipo **Short** se pueden declarar como **signed** Short o **unsigned short**. **Signed Short** es un sinónimo de **Short**.|
||**int**|El tipo **int** es un tipo entero que es mayor o igual que el tamaño del tipo **Short int**, y menor o igual que el tamaño del tipo **Long**.<br /><br /> Los objetos de tipo **int** se pueden declarar como **signed int** o **unsigned int**. **Signed int** es un sinónimo de **int**.|
||**__int8**, **__int16**, **__int32**, **__int64**|En el entero con tamaño `__int n`, `n` es el tamaño, en bits, de la variable de entero. **__int8**, **__int16**, **__int32** y **__int64** son palabras clave específicas de Microsoft. No todos los tipos están disponibles en todas las arquitecturas. (no se admite **__int128** ).|
||**long**|El tipo **Long** (o **Long int**) es un tipo entero que es mayor o igual que el tamaño de tipo **int**. (En Windows **Long** tiene el mismo tamaño que **int**).<br /><br /> Los objetos de tipo **Long** se pueden declarar como **signed Long** o **unsigned Long**. **Signed Long** es un sinónimo de **Long**.|
||**long long**|Mayor que un entero **largo**sin signo.<br /><br /> Los objetos de tipo **Long Long** se pueden declarar como **signed** Long Long o **unsigned Long Long**. **signed Long** Long es un sinónimo de Long **Long**.|
||**wchar_t**, **__wchar_t**|Una variable de tipo **wchar_t** designa un tipo de caracteres anchos o multibyte. De forma predeterminada, **wchar_t** es un tipo nativo, pero se puede usar [/Zc: wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para hacer **wchar_t** un typedef para **unsigned short**. El tipo de **__wchar_t** es un sinónimo específico de Microsoft para el tipo de **wchar_t** nativo.<br /><br /> Use el prefijo L delante de un carácter o un literal de cadena para designar el tipo de carácter ancho.|
|Punto flotante|**float**|El tipo **float** es el tipo de punto flotante más pequeño.|
||**double**|El tipo **Double** es un tipo de punto flotante que es mayor o igual que el tipo **float**, pero menor o igual que el tamaño del tipo **Long Double**.<br /><br /> Específico de Microsoft: la representación de **Long Double** y **Double** es idéntica. Sin embargo, **Long Double** y **Double** son tipos independientes.|
||**long double**|Tipo **Long Double** es un tipo de punto flotante que es mayor o igual que el tipo **Double**.|

**Específicos de Microsoft**

En la tabla siguiente se muestra la cantidad de almacenamiento necesaria para los tipos fundamentales de Microsoft C++.

### <a name="sizes-of-fundamental-types"></a>Tamaños de los tipos fundamentales

|Tipo de|Tamaño de la|
|----------|----------|
|**bool**, **Char**, **unsigned char**, **signed char**, **__int8**|1 byte|
|**__int16**, **Short**, **unsigned short**, **wchar_t**, **__wchar_t**|2 bytes|
|**float**, **__int32**, **int**, **unsigned int**, **Long**, **unsigned Long**|4 bytes|
|**Double**, **__int64**, **Long Double**, Long **Long**|8 bytes|

**FIN de Específicos de Microsoft**

Vea [Intervalos de tipo de datos](../cpp/data-type-ranges.md) para obtener un resumen del intervalo de valores de cada tipo.

Para obtener más información sobre la conversión de tipos, vea [Conversiones estándar](../cpp/standard-conversions.md).

## <a name="see-also"></a>Vea también

[Intervalos de tipo de datos](../cpp/data-type-ranges.md)