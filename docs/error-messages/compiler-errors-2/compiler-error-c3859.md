---
title: Error del compilador C3859 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2f8c51f25c09881e10e980276fc2035a6a70aed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272310"
---
# <a name="compiler-error-c3859"></a>Error del compilador C3859
se superó el intervalo de memoria virtual de PCH; vuelva a compilarlo con una opción de la línea de comandos de '-Zmvalue' o superior  
  
 El encabezado precompilado es demasiado pequeño para la cantidad de datos que el compilador está tratando de incluir en él. Use la **/Zm** marca de compilador para especificar un valor mayor para el archivo de encabezado precompilado. Para obtener más información, consulte [/Zm (especificar memoria asignación límite de encabezado precompilado)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).