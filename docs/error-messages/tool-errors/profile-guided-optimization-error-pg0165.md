---
title: Error de la optimización guiada por perfiles PG0165
ms.date: 11/04/2016
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: f39bbe6540ebec10cd25c41ac2fe9f2acfca9b13
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434529"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Error de la optimización guiada por perfiles PG0165

Leer 'Filename.pgd': ' no se admite la versión PGD (error de coincidencia de versión)'.

Archivos PGD son específicos para un conjunto de herramientas del compilador determinado. Este error se genera cuando se usa un compilador distinto del que se utilizó para *Filename*pgd. Este error indica que este conjunto de herramientas del compilador no puede usar los datos de *Filename*.pgd para optimizar el programa actual.

Para resolver este problema, vuelva a generar *Filename*.pgd mediante el conjunto de herramientas del compilador actual.