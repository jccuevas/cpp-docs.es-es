---
title: Error del compilador C3859
ms.date: 03/08/2019
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: 9b20224207ba797c6ee93c06404e4d90c3d02525
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738652"
---
# <a name="compiler-error-c3859"></a>Error del compilador C3859

> intervalo de memoria virtual para PCH superado; Vuelva a compilarlo con una opción de línea de comandos de '-Zm*valor*' o superior

La memoria virtual asignada para el encabezado precompilado es demasiado pequeña para la cantidad de datos que el compilador está intentando incluir en él. A partir de Visual Studio 2015, el **/Zm** recomendación solo es significativa cuando se usa el `#pragma hdrstop` directiva. En otros casos, es un error falso que indique problemas de presión de memoria virtual de Windows.

Si usa el encabezado precompilado un `#pragma hdrstop` la directiva, use el **/Zm** marca de compilador para especificar un valor mayor para el archivo de encabezado precompilado. De lo contrario, considere la posibilidad de reducir el número de procesos de compilación paralela en la compilación. Para obtener más información, consulte [/Zm (especificar precompilado encabezado memoria límite de asignación)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).
