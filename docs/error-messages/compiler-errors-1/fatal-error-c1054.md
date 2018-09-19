---
title: Error irrecuperable C1054 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 439019b1f510127ae54e77d445d59e86be09a49b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101974"
---
# <a name="fatal-error-c1054"></a>Error irrecuperable C1054

límite del compilador: los inicializadores están demasiado anidados

El código supera el límite de anidamiento de inicializadores (10-15 niveles, dependiendo de la combinación de tipos que se está inicializando).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Simplifique los tipos de datos que se está inicializando para reducir el anidamiento.

1. Inicialice las variables en instrucciones independientes después de la declaración.