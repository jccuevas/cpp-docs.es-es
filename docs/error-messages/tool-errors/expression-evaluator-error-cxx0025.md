---
title: Error del evaluador de expresiones CXX0025 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0025
dev_langs:
- C++
helpviewer_keywords:
- CAN0025
- CXX0025
ms.assetid: 3e2fb541-63b3-46ac-9f93-3dadb253bcf6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd89faa4de7b296d6a6771f857f3d16dbe2f94f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043708"
---
# <a name="expression-evaluator-error-cxx0025"></a>Error del evaluador de expresiones CXX0025

operador necesita struct/union

Un operador que toma una expresión de `struct` o **unión** tipo se aplicó a una expresión que no es un `struct` o **union**.

Componentes de la clase, estructura o unión variables deben tener un nombre completo. No se pueden especificar los componentes sin especificación completa.

Este error es idéntico a CAN0025.