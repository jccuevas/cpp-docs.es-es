---
title: Error grave de NMAKE U1064 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4240bf2c553957e73d5ead0bdd03ea129450645b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093004"
---
# <a name="nmake-fatal-error-u1064"></a>Error grave de NMAKE U1064

Archivo MAKE no se encuentra y se especificó ningún destino

La línea de comandos NMAKE no especificó un archivo MAKE o un destino y el directorio actual no contiene un archivo denominado archivo MAKE.

NMAKE requiere un archivo MAKE o un destino de línea de comandos (o ambos). Para que esté disponible un archivo MAKE NMAKE, especifique la opción /F o coloque un archivo denominado MAKE en el directorio actual. NMAKE puede crear un destino de línea de comandos mediante una regla de inferencia si no se proporciona un archivo MAKE.