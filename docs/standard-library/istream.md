---
title: '&lt;istream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
dev_langs:
- C++
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7000bd30e34836466e9f662f9b6b0dd8f2ecde4c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956559"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Define el basic_istream de clase de plantilla que remita extracciones para las iostreams, y el basic_iostream de clase de plantilla que remita las inserciones y extracciones. El encabezado define también un manipulador relacionado. Este archivo de encabezado se suele incluir automáticamente mediante otro encabezado de iostreams; rara vez tendrá que incluirlo directamente.

## <a name="syntax"></a>Sintaxis

```cpp
#include <istream>

```

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Un tipo `basic_iostream` especializado en **char**.|
|[istream](../standard-library/istream-typedefs.md#istream)|Un tipo `basic_istream` especializado en **char**.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Tipo `basic_iostream` especializado en **wchar**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Tipo `basic_istream` especializado en **wchar**.|

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Omite los espacios en blanco en el flujo.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Intercambia dos objetos de flujo.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Extrae caracteres y cadenas del flujo.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Clase de secuencia que puede realizar tanto operaciones de entrada como de salida.|
|[basic_istream](../standard-library/basic-istream-class.md)|La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia con elementos de tipo `Elem`, también conocida como [char_type](../standard-library/basic-ios-class.md#char_type), cuyos rasgos de caracteres están determinados por la clase `Tr`, también conocida como [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
