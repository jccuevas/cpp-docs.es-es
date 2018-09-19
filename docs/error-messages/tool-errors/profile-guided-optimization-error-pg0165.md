---
title: Error de optimización por perfiles PG0165 guiada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PG0165
dev_langs:
- C++
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 332751a123bf7d6414c40b79870b5edf27a3d8a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084216"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Error de la optimización guiada por perfiles PG0165

Leer 'Filename.pgd': ' no se admite la versión PGD (error de coincidencia de versión)'.

Archivos PGD son específicos para un conjunto de herramientas del compilador determinado. Este error se genera cuando se usa un compilador distinto del que se utilizó para *Filename*pgd. Este error indica que este conjunto de herramientas del compilador no puede usar los datos de *Filename*.pgd para optimizar el programa actual.

Para resolver este problema, vuelva a generar *Filename*.pgd mediante el conjunto de herramientas del compilador actual.