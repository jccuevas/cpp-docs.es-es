---
title: Error del compilador C2410 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba4c2b57bcae062ccf811e33cf1deaea45f83737
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052457"
---
# <a name="compiler-error-c2410"></a>Error del compilador C2410

'identifier': nombre de miembro ambiguo en 'contexto'

El identificador es un miembro de más de una estructura o unión en este contexto.

Usar un especificador de estructura o unión en el operando que produjo el error. Un especificador de estructura o unión es un identificador de tipo `struct` o `union` (un `typedef` nombre o una variable del mismo tipo que la estructura o unión que se hace referencia). El especificador debe ser el operando izquierdo de la primer operador de selección de miembro (.) para usar el operando.