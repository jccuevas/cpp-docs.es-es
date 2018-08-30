---
title: '&lt;streambuf&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <streambuf>
dev_langs:
- C++
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db05d1b19a67fc54a148d407fd90992a6d37c4c6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213592"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Incluya el encabezado estándar de iostreams \<streambuf> para definir la clase de plantilla [basic_streambuf](../standard-library/basic-streambuf-class.md), que es fundamental para el funcionamiento de las clases de iostreams. Este encabezado se suele incluir automáticamente mediante otro de los encabezados de iostreams; rara vez tendrá que incluirlo directamente.

## <a name="syntax"></a>Sintaxis

```cpp
#include <streambuf>

```

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Una especialización de `basic_streambuf` que usa **char** como los parámetros de plantilla.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Una especialización de `basic_streambuf` que usa **wchar_t** como los parámetros de plantilla.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[basic_streambuf (Clase)](https://msdn.microsoft.com/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|La clase de plantilla describe una clase base abstracta para derivar un búfer de secuencia, que controla la transmisión de elementos a y desde una representación concreta de una secuencia.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Programación con iostream](../standard-library/iostream-programming.md)<br/>
[Convenciones de iostreams](../standard-library/iostreams-conventions.md)<br/>
