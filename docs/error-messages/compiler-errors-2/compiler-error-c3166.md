---
title: Error del compilador C3166 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3166
dev_langs:
- C++
helpviewer_keywords:
- C3166
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c568f1732a4be5d890a5a654b09638828385383
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035518"
---
# <a name="compiler-error-c3166"></a>Error del compilador C3166

'pointer': no se puede declarar un puntero a un puntero __gc interior como miembro de 'type'

El compilador encontró una declaración de puntero no válido (un `__nogc` puntero a un `__gc` puntero.).

Solo es accesible a través de la opción del compilador obsoleto C3166 **/CLR: oldSyntax**.
