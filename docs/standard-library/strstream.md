---
title: '&lt;strstream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <strstream>
dev_langs:
- C++
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1695306ddc53a8150917eef8b27f5d3edce2bf3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961869"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

Define varias clases que admiten operaciones de iostreams en secuencias almacenadas en una matriz asignada de **char** objeto. Estas secuencias se convierten fácilmente a y desde cadenas de C.

## <a name="syntax"></a>Sintaxis

```cpp
#include <strstream>

```

## <a name="remarks"></a>Comentarios

Los objetos de tipo `strstream` funcionan con `char` *, que son cadenas de C. Use [\<sstream>](../standard-library/sstream.md) para trabajar con objetos de tipo [basic_string](../standard-library/basic-string-class.md).

> [!NOTE]
> Las clases de \<strstream > están en desuso. Considere el uso de las clases de \<sstream > en su lugar.

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[strstreambuf (Clase)](../standard-library/strstreambuf-class.md)|La clase describe un búfer de secuencia que controla la transmisión de elementos a y desde una secuencia de elementos almacenados en un **char** objeto array.|
|[istrstream (Clase)](../standard-library/istrstream-class.md)|La clase describe un objeto que controla la extracción de objetos codificados y elementos de un búfer de secuencia de la clase [strstreambuf](../standard-library/strstreambuf-class.md).|
|[ostrstream (Clase)](../standard-library/ostrstream-class.md)|La clase describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia de la clase [strstreambuf](../standard-library/strstreambuf-class.md).|
|[strstream (Clase)](../standard-library/strstream-class.md)|La clase describe un objeto que controla la inserción y la extracción de objetos codificados y elementos mediante un búfer de secuencia de la clase [strstreambuf](../standard-library/strstreambuf-class.md).|

## <a name="see-also"></a>Vea también

[\<strstream>](../standard-library/strstream.md)<br/>
[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
