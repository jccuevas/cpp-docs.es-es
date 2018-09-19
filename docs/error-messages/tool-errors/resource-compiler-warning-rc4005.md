---
title: Advertencia del compilador de recursos RC4005 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 589fd008b3927887a8144b2fc63d2cbbde2af913
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028524"
---
# <a name="resource-compiler-warning-rc4005"></a>Advertencia del compilador de recursos RC4005

'identifier': redefinición de macro

El identificador se define dos veces. El compilador usa la segunda definición de macro.

Esta advertencia puede deberse a la definición de una macro en la línea de comandos y en el código con un `#define` directiva. También puede deberse a macros importadas desde los archivos de inclusión.

Para eliminar la advertencia, quite una de las definiciones o use un `#undef` la directiva antes de la segunda definición.