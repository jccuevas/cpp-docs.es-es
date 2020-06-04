---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: ca5f53d67bb32e59c20d1d440879144f0a617c66
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686022"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Incluya el encabezado estándar iostreams \<streambuf > para definir la plantilla de clase [basic_streambuf](../standard-library/basic-streambuf-class.md), que es básica para el funcionamiento de las clases iostreams. Este encabezado se suele incluir automáticamente mediante otro de los encabezados de iostreams; rara vez tendrá que incluirlo directamente.

## <a name="syntax"></a>Sintaxis

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Una especialización de `basic_streambuf` que usa **Char** como parámetros de plantilla.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Una especialización de `basic_streambuf` que usa **wchar_t** como parámetros de plantilla.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_streambuf (Clase)](basic-streambuf-class.md)|La plantilla de clase describe una clase base abstracta para derivar un búfer de secuencia, que controla la transmisión de elementos a y desde una representación concreta de una secuencia.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
