---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 20efdc755b7f706fc6ee962daa32bd352df39d45
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522907"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

Define varias clases que admiten operaciones de iostreams en secuencias almacenadas en archivos externos.

## <a name="syntax"></a>Sintaxis

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Un tipo `basic_filebuf` especializado en **char** parámetros de plantilla.|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Un tipo `basic_fstream` especializado en **char** parámetros de plantilla.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Un tipo `basic_ifstream` especializado en **char** parámetros de plantilla.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Un tipo `basic_ofstream` especializado en **char** parámetros de plantilla.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Un tipo `basic_fstream` especializado en **wchar_t** parámetros de plantilla.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Un tipo `basic_ifstream` especializado en **wchar_t** parámetros de plantilla.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Un tipo `basic_ofstream` especializado en **wchar_t** parámetros de plantilla.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Un tipo `basic_filebuf` especializado en **wchar_t** parámetros de plantilla.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|La clase de plantilla describe un búfer de secuencia que controla la transmisión de elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`, a y desde una secuencia de elementos almacenados en un archivo externo.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|La clase de plantilla describe un objeto que controla la inserción y extracción de elementos y objetos codificados usando un búfer de secuencia de clase [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**,  **TR**>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de secuencia de clase [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|La clase de plantilla describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de secuencia de clase [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
