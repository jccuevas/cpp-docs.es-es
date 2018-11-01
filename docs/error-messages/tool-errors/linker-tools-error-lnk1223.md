---
title: Error de las herramientas del vinculador LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 331521c357389c2f7c1aa786969154a2b747ffe5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537974"
---
# <a name="linker-tools-error-lnk1223"></a>Error de las herramientas del vinculador LNK1223

archivo no válido o dañado: el archivo contiene contribuciones .pdata no válidas

En el caso de plataformas RISC que utilizan pdata, este error se produce si el compilador generó una sección .pdata con entradas no ordenadas.

Para corregir este problema, intente compilar sin [/GL (Whole Program Optimization)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) habilitado. Los cuerpos de función vacíos también pueden producir este error en algunos casos.