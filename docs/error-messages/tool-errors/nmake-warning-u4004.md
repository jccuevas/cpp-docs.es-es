---
title: Advertencia de NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 882f6c98b31d23d283f5e8b32b46a46c543b1a76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436223"
---
# <a name="nmake-warning-u4004"></a>Advertencia de NMAKE U4004

demasiadas reglas para el destino 'nombrededestino'

Se especificó más de un bloque de descripción para el destino dado mediante signos de dos puntos (**:**) como separadores. NMAKE ejecuta los comandos en el primer bloque de descripción y omite los bloques de una versión posterior.

Para especificar el mismo destino en varias dependencias, use dos puntos dobles (`::`) como separador en cada línea de dependencia.