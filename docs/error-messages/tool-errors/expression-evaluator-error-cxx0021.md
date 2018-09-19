---
title: Error del evaluador de expresiones CXX0021 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0021
dev_langs:
- C++
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ef765286d022b26aeed0ca98c9f43f94f5d17f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025781"
---
# <a name="expression-evaluator-error-cxx0021"></a>Error del evaluador de expresiones CXX0021

struct o union utilizados como escalar

Se utilizó una estructura o unión en una expresión, pero no se especificó ningún elemento.

Al manipular una estructura o variable de unión, el nombre de la variable puede aparecer por sí mismo, sin un calificador de campo. Si se usa una estructura o unión en una expresión, se deben calificar con el elemento específico deseado.

Especifique el elemento cuyo valor es que se usará en la expresión.

Este error es idéntico a CAN0021.