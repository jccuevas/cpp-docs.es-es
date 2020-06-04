---
title: Error de las herramientas del vinculador LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 9c9d4c7224a7e65775354a86bd34fa9ea1b074af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195037"
---
# <a name="linker-tools-error-lnk1223"></a>Error de las herramientas del vinculador LNK1223

archivo no válido o dañado: el archivo contiene contribuciones .pdata no válidas

En el caso de plataformas RISC que utilizan pdata, este error se produce si el compilador generó una sección .pdata con entradas no ordenadas.

Para solucionar este problema, pruebe a compilar sin [/GL (optimización de todo el programa)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) habilitada. Los cuerpos de función vacíos también pueden producir este error en algunos casos.
