---
title: Tipos fundamentales (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __wchar_t_cpp
- long_double_cpp
- unsigned
- wchar_t_cpp
- float_cpp
- wchar_t
- char
- char_cpp
- signed
- __wchar_t
- signed_cpp
- short
- double_cpp
- int_cpp
- long
- __intn_cpp
- short_cpp
- double
- unsigned_cpp
- float
- __intn
- long_cpp
- int
- long_double
- unsigned_int
- __int8
- __int8_cpp
- __int16
- __int16_cpp
- __int32
- __int32_cpp
- __int64
- __int64_cpp
- __int128
- __int128_cpp
dev_langs:
- C++
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type, C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type
- double data type, summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers, C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++], C++ data types
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 595c2d84ad18cae0c15ddba36388f66f10fecd49
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="fundamental-types--c"></a>Tipos fundamentales (C++)
Los tipos fundamentales de C++ se dividen en tres categorías: entero, punto flotante y void. Los tipos enteros son capaces de controlar números enteros. Los tipos de punto flotante son capaces de especificar valores que pueden tener partes fraccionarias.  
  
 El tipo [void](../cpp/void-cpp.md) describe un conjunto de valores vacío. No se puede especificar ninguna variable de tipo `void` ; se utiliza principalmente para declarar funciones que no devuelven ningún valor o para declarar punteros genéricos a datos sin tipo o con un tipo arbitrario. Cualquier expresión se puede convertir explícitamente al tipo `void`. Sin embargo, estas expresiones se limitan a los siguientes usos:  
  
-   Una instrucción de expresión. (Vea [Expresiones](../cpp/expressions-cpp.md)para obtener más información).  
  
-   El operando izquierdo del operador de coma. (Vea [Operador de coma](../cpp/comma-operator.md) para obtener más información).  
  
-   El segundo o tercer operando del operador condicional (`? :`). (Vea [Expresiones con el operador condicional](../cpp/conditional-operator-q.md) para obtener más información).  
  
 En la tabla siguiente se explican las restricciones en los tamaños de tipo. Estas restricciones son independientes de la implementación de Microsoft.  
  
### <a name="fundamental-types-of-the-c-language"></a>Tipos fundamentales del lenguaje C++  
  
|Categoría|Tipo|Contenido|  
|--------------|----------|--------------|  
|Entero|`char`|El tipo `char` es un tipo entero que normalmente contiene miembros del juego de caracteres de la ejecución básica que, de forma predeterminada, es ASCII, en Microsoft C++.<br /><br /> El compilador de C++ trata las variables del tipo `char`, `signed` `char`y `unsigned` `char` como si tuvieran tipos diferentes. Las variables del tipo `char` se promueven a `int` como si fueran del tipo `signed` `char` de forma predeterminada, a menos que se use la opción de compilación /J. En ese caso se tratan como tipo `unsigned` `char` y se promueven a `int` sin la extensión de signo.|  
||`bool`|El tipo `bool` es un tipo entero que puede tener uno de dos valores: `true` o `false`. Su tamaño no está especificado.|  
||`short`|El tipo `short` `int` (o simplemente `short`) es un tipo entero que es superior o igual al tamaño del tipo `char`e inferior o igual al tamaño del tipo `int`.<br /><br /> Los objetos del tipo `short` se pueden declarar como `signed` `short` o `unsigned short`. `Signed short` es un sinónimo de `short`.|  
||`int`|El tipo `int` es un tipo entero que es superior o igual al tamaño del tipo `short` `int`e inferior o igual al tamaño del tipo `long`.<br /><br /> Los objetos del tipo `int` se pueden declarar como `signed` `int` o `unsigned` `int`. `Signed` `int` es un sinónimo de `int`.|  
||`__int8`, `__int16`, `__int32`, `__int64`|En el entero con tamaño `__int n`, `n` es el tamaño, en bits, de la variable de entero. `__int8`, `__int16`, `__int32` y `__int64` son palabras clave específicas de Microsoft. No todos los tipos están disponibles en todas las arquitecturas. `(__int128`no se admite.)|  
||`long`|El tipo `long` (o `long` `int`) es un tipo entero que es superior o igual al tamaño del tipo `int`.<br /><br /> Los objetos del tipo `long` se pueden declarar como `signed` `long` o `unsigned` `long`. `Signed` `long` es un sinónimo de `long`.|  
||`long` `long`|Mayor que `long`sin signo.<br /><br /> Los objetos del tipo `long long` se pueden declarar como `signed` `long long` o `unsigned` `long long`. `Signed` `long long` es un sinónimo de `long long`.|  
||`wchar_t`, `__wchar_t`|Una variable del tipo `wchar_t` indica un carácter ancho o multibyte. De forma predeterminada, `wchar_t` es un tipo nativo, pero se puede usar [/Zc:wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para convertir `wchar_t` en una typedef para `unsigned short`. El `__wchar_t` tipo es un sinónimo específico de Microsoft para el tipo `wchar_t` nativo.<br /><br /> Use el prefijo L delante de un carácter o un literal de cadena para designar el tipo de carácter ancho.|  
|Punto flotante|`float`|El tipo `float` es el tipo de punto flotante más pequeño.|  
||`double`|El tipo `double` es un tipo flotante superior o igual al tipo `float`, pero inferior o igual al tamaño del tipo `long` `double`.<br /><br /> Específico de Microsoft: la representación de `long double` y `double` es idéntica. Sin embargo, `long double` y `double` son tipos distintos.|  
||`long double`|El tipo `long` `double` es un tipo de punto flotante que es superior o igual al tipo `double`.|  
  
 **Específicos de Microsoft**  
  
 En la tabla siguiente se muestra la cantidad de almacenamiento necesaria para los tipos fundamentales de Microsoft C++.  
  
### <a name="sizes-of-fundamental-types"></a>Tamaños de los tipos fundamentales  
  
|Tipo|Tamaño|  
|----------|----------|  
|`bool`, `char`, `unsigned char`, `signed char`, `__int8`|1 byte|  
|`__int16`, `short`, `unsigned short`, `wchar_t`, `__wchar_t`|2 bytes|  
|`float`, `__int32`, `int`, `unsigned int`, `long`, `unsigned long`|4 bytes|  
|`double`, `__int64`, `long double`, `long long`|8 bytes|  
  
 **FIN de Específicos de Microsoft**  
  
 Vea [Intervalos de tipo de datos](../cpp/data-type-ranges.md) para obtener un resumen del intervalo de valores de cada tipo.  
  
 Para obtener más información sobre la conversión de tipos, vea [Conversiones estándar](../cpp/standard-conversions.md).  
  
## <a name="see-also"></a>Vea también  
 [Intervalos de tipo de datos](../cpp/data-type-ranges.md)
