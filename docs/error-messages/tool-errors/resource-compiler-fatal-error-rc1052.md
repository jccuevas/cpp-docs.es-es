---
title: Error irrecuperable del compilador de recursos RC1052
ms.date: 11/04/2016
f1_keywords:
- RC1052
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
ms.openlocfilehash: 2ab9dd48420ca263abbf3da22da878a3e74a2151
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488418"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Error irrecuperable del compilador de recursos RC1052

límite del compilador: los bloques #if o #ifdef están demasiado anidados

El programa superó el máximo permitido de niveles de anidamiento para las directivas `#if` y `#ifdef`.

Este error puede deberse a los archivos de inclusión que utilizan estas directivas de preprocesador.

Para solucionar este problema, reduzca el número de directivas `#if` y `#ifdef` anidadas en el archivo de recursos. Si el problema está causado por archivos de encabezado incluidos en el archivo de recursos, reduzca el número de directivas `#if` y `#ifdef` anidadas en los archivos de encabezado. Si no es posible, considere la posibilidad de crear e incluir un nuevo archivo de encabezado en el archivo de recursos, ejecutando el preprocesador en los archivos de encabezado incluidos. Para obtener más información, consulte el [/P (Preprocesar para un archivo)](../../build/reference/p-preprocess-to-a-file.md) opción del compilador.