---
title: Error del compilador de recursos RC2101
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 595e87b73d79a01993e0e9b3aaa814332b21413f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448028"
---
# <a name="resource-compiler-error-rc2101"></a>Error del compilador de recursos RC2101

Directiva no válida en el archivo RC preprocesado

El archivo del compilador de recursos contiene una **#pragma** directiva.

Use la **#ifndef** directiva de preprocesador con la constante RC_INVOKED que define el compilador de recursos cuando se procesa un archivo de inclusión. Colocar el **#pragma** directiva dentro de un bloque de código que no se procesa cuando se define la constante RC_INVOKED. Código del bloque se procesa solo por el compilador de C/C ++ y no por el compilador de recursos. Ejemplo de código siguiente muestra esta técnica:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

El **#pragma** directiva de preprocesador no tiene ningún significado una. Archivo RC. El **#include** directiva de preprocesador se usa con frecuencia en una. Archivo RC para incluir un archivo de encabezado (un archivo de encabezado personalizado basado en el proyecto o un archivo de encabezado estándar proporcionado por Microsoft con uno de sus productos). Algunos de estos archivos de inclusión contienen la **#pragma** directiva. Dado que un archivo de encabezado puede incluir uno o varios archivos de encabezado, el archivo que contiene la provoca el error **#pragma** directiva puede no ser evidente de inmediato.

El **#ifndef** RC_INVOKED puede controlar archivos de encabezado en archivos de encabezado basados en proyectos de inclusión.