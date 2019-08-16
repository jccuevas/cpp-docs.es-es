---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 87fb74f62abffdd62b8c0179b13f53d96439d6c6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449578"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Incluya el encabezado estándar de iostreams \<streambuf> para definir la clase de plantilla [basic_streambuf](../standard-library/basic-streambuf-class.md), que es fundamental para el funcionamiento de las clases de iostreams. Este encabezado se suele incluir automáticamente mediante otro de los encabezados de iostreams; rara vez tendrá que incluirlo directamente.

## <a name="syntax"></a>Sintaxis

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|DESCRIPCIÓN|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Una especialización de `basic_streambuf` que usa **Char** como parámetros de plantilla.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Especialización de `basic_streambuf` que usa **wchar_t** como parámetros de plantilla.|

### <a name="classes"></a>Clases

|Clase|DESCRIPCIÓN|
|-|-|
|[basic_streambuf (Clase)](basic-streambuf-class.md)|La clase de plantilla describe una clase base abstracta para derivar un búfer de secuencia, que controla la transmisión de elementos a y desde una representación concreta de una secuencia.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
