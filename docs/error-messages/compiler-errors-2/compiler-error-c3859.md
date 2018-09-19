---
title: Error del compilador C3859 | Microsoft Docs
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
ms.openlocfilehash: 1ac06a09a6ad66384fd2b5423e3df046771f7653
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053394"
---
# <a name="compiler-error-c3859"></a>Error del compilador C3859

se superó el intervalo de memoria virtual de PCH; vuelva a compilarlo con una opción de la línea de comandos de '-Zmvalue' o superior

El encabezado precompilado es demasiado pequeño para la cantidad de datos que el compilador está tratando de incluir en él. Use la **/Zm** marca de compilador para especificar un valor mayor para el archivo de encabezado precompilado. Para obtener más información, consulte [/Zm (especificar precompilado encabezado memoria límite de asignación)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).