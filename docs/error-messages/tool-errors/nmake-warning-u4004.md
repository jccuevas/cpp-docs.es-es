---
title: Advertencia de NMAKE U4004 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a89bb8abf212c8a0ffa9fb40fe5d3ea43307a08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016655"
---
# <a name="nmake-warning-u4004"></a>Advertencia de NMAKE U4004

demasiadas reglas para el destino 'nombrededestino'

Se especificó más de un bloque de descripción para el destino dado mediante signos de dos puntos (**:**) como separadores. NMAKE ejecuta los comandos en el primer bloque de descripción y omite los bloques de una versión posterior.

Para especificar el mismo destino en varias dependencias, use dos puntos dobles (`::`) como separador en cada línea de dependencia.