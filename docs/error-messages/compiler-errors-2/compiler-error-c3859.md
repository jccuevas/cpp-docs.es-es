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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8a132eb7dbf09421ad5c99249b0208e5f901156b
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3859"></a>Error del compilador C3859
se superó el intervalo de memoria virtual de PCH; vuelva a compilarlo con una opción de la línea de comandos de '-Zmvalue' o superior  
  
 El encabezado precompilado es demasiado pequeño para la cantidad de datos que el compilador está tratando de incluir en él. Use la **/Zm** marca de compilador para especificar un valor mayor para el archivo de encabezado precompilado. Para obtener más información, consulte [/Zm (especificar memoria asignación límite de encabezado precompilado)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).
