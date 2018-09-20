---
title: 2.7.2.4 compartido | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d1a545f1c505f9f578cad682399c8d69a882824
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400151"
---
# <a name="2724-shared"></a>2.7.2.4 shared

Esta cláusula comparte las variables que aparecen en la *variable lista* entre todos los subprocesos en un equipo. Todos los subprocesos dentro de un equipo obtener acceso a la misma área de almacenamiento para **compartido** variables.

La sintaxis de la **compartido** cláusula es como sigue:

```
shared(variable-list)
```