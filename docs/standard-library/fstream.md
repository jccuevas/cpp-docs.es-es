---
title: '&lt;fstream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <fstream>
dev_langs:
- C++
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b716248c6fe9d0734cd580800c9254cf01f2a17
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962879"
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
