---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 1f85367b9ae527c9387d085acc1496bfbbf7cc9e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688034"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

Define varias clases que admiten operaciones de iostreams en secuencias almacenadas en archivos externos.

## <a name="syntax"></a>Sintaxis

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Tipo `basic_filebuf` especializado en parámetros de plantilla **Char** .|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Tipo `basic_fstream` especializado en parámetros de plantilla **Char** .|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Tipo `basic_ifstream` especializado en parámetros de plantilla **Char** .|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Tipo `basic_ofstream` especializado en parámetros de plantilla **Char** .|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Tipo `basic_fstream` especializado en parámetros de plantilla **wchar_t** .|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Tipo `basic_ifstream` especializado en parámetros de plantilla **wchar_t** .|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Tipo `basic_ofstream` especializado en parámetros de plantilla **wchar_t** .|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Tipo `basic_filebuf` especializado en parámetros de plantilla **wchar_t** .|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|La plantilla de clase describe un búfer de secuencia que controla la transmisión de elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`, a y desde una secuencia de elementos almacenados en un archivo externo.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|La plantilla de clase describe un objeto que controla la inserción y extracción de elementos y objetos codificados mediante un búfer de secuencia de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, con elementos de tipo `Elem`, cuyo carácter los rasgos vienen determinados por la clase `Tr`.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|La plantilla de clase describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, con elementos de tipo `Elem`, cuyos rasgos de caracteres son viene determinado por la clase `Tr`.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|La plantilla de clase describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia de clase [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, con elementos de tipo `Elem`, cuyos rasgos de caracteres se determinan por la clase `Tr`.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programación con iostream](../standard-library/iostream-programming.md)\
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)
