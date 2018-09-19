---
title: Error grave de NMAKE U1100 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1100
dev_langs:
- C++
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27ffd33a0a80056ee57f5f088823d7f8f6549c24
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135774"
---
# <a name="nmake-fatal-error-u1100"></a>Error grave de NMAKE U1100

la macro 'nombredemacro' no es válida en el contexto de la regla por lotes 'regla'

NMAKE genera este error cuando el bloque de comandos de una regla de modo por lotes directa o indirectamente hace referencia a una macro de archivo especial que no es de $<.

$< solo se permite la macro para las reglas de modo por lotes.