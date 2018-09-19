---
title: Error del compilador de recursos RC2151 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a15f3f1237df9e4b706a2c2048dddd6d5db395d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109787"
---
# <a name="resource-compiler-error-rc2151"></a>Error del compilador de recursos RC2151

No se puede volver a usar las constantes de cadena

Utiliza el mismo valor dos veces en un **STRINGTABLE** instrucción. Asegúrese de que no mezcla superpuestos valores hexadecimales y decimales.

Cada identificador en un **STRINGTABLE** deben ser únicos. Para lograr la máxima eficacia uso contiguos las constantes que se inician en un múltiplo de 16.