---
title: '&lt;fstream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <fstream>
dev_langs:
- C++
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe86803f986853335fbad15e0c3323d9365d381
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Un tipo `basic_filebuf` especializado en parámetros de plantilla `char`.|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Un tipo `basic_fstream` especializado en parámetros de plantilla `char`.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Un tipo `basic_ifstream` especializado en parámetros de plantilla `char`.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Un tipo `basic_ofstream` especializado en parámetros de plantilla `char`.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Un tipo `basic_fstream` especializado en parámetros de plantilla `wchar_t`.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Un tipo `basic_ifstream` especializado en parámetros de plantilla `wchar_t`.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Un tipo `basic_ofstream` especializado en parámetros de plantilla `wchar_t`.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Un tipo `basic_filebuf` especializado en parámetros de plantilla `wchar_t`.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|La clase de plantilla describe un búfer de flujo que controla la transmisión de elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr**, a y desde una secuencia de elementos almacenados en un archivo externo.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|La clase de plantilla describe un objeto que controla la inserción y la extracción de elementos y objetos codificados de un búfer de flujo de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr**.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr**.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|La clase de plantilla describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de flujo de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr**.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
