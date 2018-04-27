---
title: '&lt;istream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ed7f0eabe0fb67177197f8bb30eb258acd0e38f
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
|[iostream](../standard-library/istream-typedefs.md#iostream)|Tipo `basic_iostream` especializado en `char`.|
|[istream](../standard-library/istream-typedefs.md#istream)|Tipo `basic_istream` especializado en `char`.|
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
|[basic_istream](../standard-library/basic-istream-class.md)|La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo con elementos de tipo **Elem**, también conocido como [char_type](../standard-library/basic-ios-class.md#char_type), cuyos rasgos de caracteres están determinados por la clase **Tr**, también conocida como [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
