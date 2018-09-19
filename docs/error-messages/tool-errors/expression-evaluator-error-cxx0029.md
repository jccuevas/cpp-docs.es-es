---
title: Error del evaluador de expresiones CXX0029 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0029
dev_langs:
- C++
helpviewer_keywords:
- CXX0029
- CAN0029
ms.assetid: 562b2132-e9cb-4591-a5bf-bc7179a7f40e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 687708db71eedf9b8f62dc88efc1bfe473cde1d4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017019"
---
# <a name="expression-evaluator-error-cxx0029"></a>Error del evaluador de expresiones CXX0029

no es puntero struct

El operador de selección de miembro (**->**) se aplicó a una expresión que no es un puntero a una estructura.

Compruebe que toda la expresión está entre paréntesis correctamente, o el tipo puede convertir la expresión de dirección para el tipo de puntero de la estructura adecuada.

Este error es idéntico a CAN0029.