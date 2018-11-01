---
title: 2.7.2.4 shared
ms.date: 11/04/2016
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
ms.openlocfilehash: ae470f4be67fac57146017d3e2791f6f95aa61b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583448"
---
# <a name="2724-shared"></a>2.7.2.4 shared

Esta cláusula comparte las variables que aparecen en la *variable lista* entre todos los subprocesos en un equipo. Todos los subprocesos dentro de un equipo obtener acceso a la misma área de almacenamiento para **compartido** variables.

La sintaxis de la **compartido** cláusula es como sigue:

```
shared(variable-list)
```