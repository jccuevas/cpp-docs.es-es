---
title: Error del compilador C2873 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2873
dev_langs:
- C++
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf0cc5663d81d6c1e7ad6a9f1a5f7ca167f12909
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049909"
---
# <a name="compiler-error-c2873"></a>Error del compilador C2873

'símbolo': símbolo no se puede usar en una declaración using

Un `using` directiva falta un [espacio de nombres](../../cpp/namespaces-cpp.md) palabra clave. Esto hace que el compilador interprete el código como incorrectamente un [mediante declaración](../../cpp/using-declaration.md) en lugar de un [#using](../../cpp/namespaces-cpp.md#using_directives).