---
title: Error irrecuperable C1107 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1107
dev_langs:
- C++
helpviewer_keywords:
- C1107
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc896f08ac161cae4e4fab5e991da810f3faf195
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016642"
---
# <a name="fatal-error-c1107"></a>Error irrecuperable C1107

no se pudo encontrar el ensamblado 'archivo': especifique la ruta de búsqueda del ensamblado utilizando /AI o estableciendo la variable de entorno LIBPATH

Se pasó un archivo de metadatos para un [#using](../../preprocessor/hash-using-directive-cpp.md) directiva que el compilador no pudo encontrar.

LIBPATH, que se describe en el tema de `#using`y el [/AI](../../build/reference/ai-specify-metadata-directories.md) opción del compilador le permiten especificar los directorios en el que el compilador buscará archivos de metadatos que se hace referencia.