---
title: Advertencia de NMAKE U4004
ms.date: 11/04/2016
f1_keywords:
- U4004
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
ms.openlocfilehash: 882f6c98b31d23d283f5e8b32b46a46c543b1a76
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298157"
---
# <a name="nmake-warning-u4004"></a>Advertencia de NMAKE U4004

demasiadas reglas para el destino 'nombrededestino'

Se especificó más de un bloque de descripción para el destino dado mediante signos de dos puntos (**:**) como separadores. NMAKE ejecuta los comandos en el primer bloque de descripción y omite los bloques de una versión posterior.

Para especificar el mismo destino en varias dependencias, use dos puntos dobles (`::`) como separador en cada línea de dependencia.