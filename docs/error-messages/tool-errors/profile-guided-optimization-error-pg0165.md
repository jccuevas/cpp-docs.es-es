---
title: Error de la optimización guiada por perfiles PG0165
ms.date: 11/04/2016
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: f39bbe6540ebec10cd25c41ac2fe9f2acfca9b13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359740"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Error de la optimización guiada por perfiles PG0165

Leer 'Filename.pgd': ' No se admite la versión PGD (error de coincidencia de versión)'.

Archivos PGD son específicos para un conjunto de herramientas del compilador determinado. Este error se genera cuando se usa un compilador distinto del que se utilizó para *Filename*pgd. Este error indica que este conjunto de herramientas del compilador no puede usar los datos de *Filename*.pgd para optimizar el programa actual.

Para resolver este problema, vuelva a generar *Filename*.pgd mediante el conjunto de herramientas del compilador actual.