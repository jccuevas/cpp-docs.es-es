---
title: Error del compilador de recursos RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 900bfed9d57af0f6f5dd8fac19380bb7c382addc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190747"
---
# <a name="resource-compiler-error-rw2001"></a>Error del compilador de recursos RW2001

Directiva no válida en el archivo RC preprocesado

El archivo RC contiene una directiva de **#pragma** .

Use la Directiva de preprocesador **#ifndef** con la constante **RC_INVOKED** que el compilador de recursos define cuando procesa un archivo de inclusión. Coloque la Directiva de **#pragma** dentro de un bloque de código que no se procese cuando se define la constante de **RC_INVOKED** . El código del bloque solo lo procesa el compiladorC++ de C/y no el compilador de recursos. En el código de ejemplo siguiente se muestra esta técnica:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

La Directiva de preprocesador **#pragma** no tiene ningún significado en. Archivo RC. La Directiva de preprocesador de **#include** se usa con frecuencia en. Archivo RC para incluir un archivo de encabezado (ya sea un archivo de encabezado personalizado basado en el proyecto o un archivo de encabezado estándar proporcionado por Microsoft con uno de sus productos). Algunos de estos archivos de inclusión contienen la directiva **#pragma** . Dado que un archivo de encabezado puede incluir uno o varios archivos de encabezado, es posible que el archivo que contiene la Directiva de **#pragma** infractora no sea obvio inmediatamente.

La técnica de **RC_INVOKED de #ifndef** puede controlar la inclusión de archivos de encabezado en archivos de encabezado basados en el proyecto.
