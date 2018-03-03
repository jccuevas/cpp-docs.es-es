---
title: Error del compilador C3859 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3a240771c0b2e104ef7c51b187d4040500edaae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3859"></a>Error del compilador C3859
se superó el intervalo de memoria virtual de PCH; vuelva a compilarlo con una opción de la línea de comandos de '-Zmvalue' o superior  
  
 El encabezado precompilado es demasiado pequeño para la cantidad de datos que el compilador está tratando de incluir en él. Use la **/Zm** marca de compilador para especificar un valor mayor para el archivo de encabezado precompilado. Para obtener más información, consulte [/Zm (especificar memoria asignación límite de encabezado precompilado)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).