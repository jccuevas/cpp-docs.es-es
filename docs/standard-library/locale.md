---
title: '&lt;locale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: 71182f4a527fba0ef2c91dc84be5a8faad9fc99f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687799"
---
# <a name="ltlocalegt"></a>&lt;locale&gt;

Define plantillas de clase y funciones C++ que los programas pueden usar para encapsular y manipular diferentes convenciones culturales en relación con la representación y el formato de los datos numéricos, Monetarios y numéricos, incluida la compatibilidad con la internacionalización. para la clasificación de caracteres y la intercalación de cadenas.

## <a name="syntax"></a>Sintaxis

```cpp
#include <locale>
```

### <a name="functions"></a>Funciones

|Función|Descripción|
|-|-|
|[has_facet](../standard-library/locale-functions.md#has_facet)|Comprueba si una faceta determinada se almacena en una configuración regional especificada.|
|[isalnum](../standard-library/locale-functions.md#isalnum)|Comprueba si un elemento de una configuración regional es un carácter alfabético o numérico.|
|[isalpha](../standard-library/locale-functions.md#isalpha)|Comprueba si un elemento de una configuración regional es un carácter alfabético.|
|[iscntrl](../standard-library/locale-functions.md#iscntrl)|Comprueba si un elemento de una configuración regional es un carácter de control.|
|[isdigit](../standard-library/locale-functions.md#isdigit)|Comprueba si un elemento de una configuración regional es un carácter numérico.|
|[isgraph](../standard-library/locale-functions.md#isgraph)|Comprueba si un elemento de una configuración regional es un carácter alfabético o un signo de puntuación.|
|[islower](../standard-library/locale-functions.md#islower)|Comprueba si un elemento de una configuración regional está en minúsculas.|
|[isprint](../standard-library/locale-functions.md#isprint)|Comprueba si un elemento de una configuración regional es un carácter imprimible.|
|[ispunct](../standard-library/locale-functions.md#ispunct)|Comprueba si un elemento de una configuración regional es un carácter de signo de puntuación.|
|[isspace](../standard-library/locale-functions.md#isspace)|Comprueba si un elemento de una configuración regional es un carácter de espacio en blanco.|
|[isupper](../standard-library/locale-functions.md#isupper)|Comprueba si un elemento de una configuración regional está en mayúsculas.|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|Comprueba si un elemento de una configuración regional es un carácter usado para representar un número hexadecimal.|
|[tolower](../standard-library/locale-functions.md#tolower)|Pasa un carácter a minúsculas.|
|[toupper](../standard-library/locale-functions.md#toupper)|Pasa un carácter a mayúsculas.|
|[use_facet](../standard-library/locale-functions.md#use_facet)|Devuelve una referencia a una faceta de un tipo especificado almacenado en una configuración regional.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|Una plantilla de clase que proporciona una faceta que se usa para realizar conversiones entre codificaciones de caracteres internas y externas.|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Una clase base para la clase codecvt que se usa para definir un tipo de enumeración al que se hace referencia como `result`, que se usa como tipo de valor devuelto para las funciones miembro de la faceta para indicar el resultado de una conversión.|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta de intercalación de una configuración regional determinada, lo que permite la recuperación de información específica de un área cultural relativa a las conversiones.|
|[collate](../standard-library/collate-class.md)|Una plantilla de clase COLLATE que proporciona una faceta que controla las convenciones de ordenación de cadenas.|
|[collate_byname](../standard-library/collate-byname-class.md)|Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta de intercalación de una configuración regional determinada, lo que permite la recuperación de información específica de un área cultural relativa a las convenciones de ordenación de cadenas.|
|[ctype](../standard-library/ctype-class.md)|Una plantilla de clase que proporciona una faceta que se usa para clasificar caracteres, convertir de mayúsculas y minúsculas y entre el juego de caracteres nativo y el que usa la configuración regional.|
|[ctype \<char >](../standard-library/ctype-char-class.md)|Una clase que es una especialización explícita de la plantilla de clase `ctype<CharType>` al tipo **Char**, que describe un objeto que puede actuar como una faceta de configuración regional para caracterizar las distintas propiedades de un carácter de tipo **Char**.|
|[ctype_base](../standard-library/ctype-base-class.md)|Una clase base para la clase ctype que se utiliza para definir los tipos de enumeración usados para clasificar o comprobar caracteres individualmente o dentro de intervalos completos.|
|[ctype_byname](../standard-library/ctype-byname-class.md)|Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta ctype de una configuración regional determinada, habilitando la clasificación de caracteres y la conversión de caracteres entre mayúsculas y minúsculas y los juegos de caracteres especificados en la configuración regional y nativa.|
|[locale](../standard-library/locale-class.md)|Una clase que describe un objeto de configuración regional que encapsula la información específica de la configuración regional como un conjunto de facetas que definen colectivamente un entorno adaptado concreto.|
|[messages](../standard-library/messages-class.md)|Una plantilla de clase que describe un objeto que puede actuar como una faceta de configuración regional para recuperar mensajes localizados de un catálogo de mensajes internacionalizados para una configuración regional determinada.|
|[messages_base](../standard-library/messages-base-class.md)|Una clase base que describe un tipo **int** para el catálogo de mensajes.|
|[messages_byname](../standard-library/messages-byname-class.md)|Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta de mensaje de una configuración regional determinada, lo que permite la recuperación de mensajes localizados.|
|[money_base](../standard-library/money-base-class.md)|Una clase base para la clase ctype que se utiliza para definir los tipos de enumeración usados para clasificar o comprobar caracteres individualmente o dentro de intervalos completos.|
|[money_get](../standard-library/money-get-class.md)|Una plantilla de clase que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de secuencias de tipo **CharType** en valores monetarios.|
|[money_put](../standard-library/money-put-class.md)|Una plantilla de clase que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de valores monetarios en secuencias de tipo **CharType**.|
|[moneypunct](../standard-library/moneypunct-class.md)|Una plantilla de clase que describe un objeto que puede actuar como una faceta de configuración regional para describir las secuencias de tipo **CharType** que se usan para representar un campo de entrada monetario o un campo de salida monetario.|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta moneypunct de una configuración regional determinada que habilita el formato de los campos de entrada o salida monetarios.|
|[num_get](../standard-library/num-get-class.md)|Una plantilla de clase que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de secuencias de tipo **CharType** en valores numéricos.|
|[num_put](../standard-library/num-put-class.md)|Una plantilla de clase que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de valores numéricos en secuencias de tipo **CharType**.|
|[numpunct](../standard-library/numpunct-class.md)|Una plantilla de clase que describe un objeto que puede actuar como una faceta local para describir las secuencias de tipo **CharType** que se usan para representar información sobre el formato y la puntuación de expresiones numéricas y booleanas.|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta moneypunct de una configuración regional determinada que habilita el formato y la puntuación de expresiones numéricas y booleanas.|
|[time_base](../standard-library/time-base-class.md)|Una clase que actúa como clase base para las caras de la plantilla de clase time_get, que define solo el tipo enumerado dateorder y varias constantes de este tipo.|
|[time_get](../standard-library/time-get-class.md)|Una plantilla de clase que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de secuencias de tipo **CharType** en valores de hora.|
|[time_get_byname](../standard-library/time-get-byname-class.md)|Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta de configuración regional de tipo time_get \<**CharType**, **InputIterator**>.|
|[time_put](../standard-library/time-put-class.md)|Una plantilla de clase que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de valores de hora en secuencias de tipo **CharType**.|
|[time_put_byname](../standard-library/time-put-byname-class.md)|Una plantilla de clase derivada que describe un objeto que puede actuar como una faceta de configuración regional de tipo `time_put` \<**CharType**, **OutputIterator**>.|
|[wbuffer_convert (Clase)](../standard-library/wbuffer-convert-class.md)|Describe un búfer de secuencia que controla la transmisión de elementos a y desde un búfer de secuencia de bytes.|
|[wstring_convert (Clase)](../standard-library/wstring-convert-class.md)|Una plantilla de clase que realiza conversiones entre una cadena de tipo ancho y una cadena de bytes.|

## <a name="see-also"></a>Vea también

[Páginas de códigos](../c-runtime-library/code-pages.md)\
[Nombres de configuración regional, idiomas y cadenas de país/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
