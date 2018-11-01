---
title: Advertencia de las herramientas del vinculador LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: 75ca9ec92bbba1c15efc11a731b3894ea03e33dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651430"
---
# <a name="linker-tools-warning-lnk4001"></a>Advertencia de las herramientas del vinculador LNK4001

ningún archivo objeto especificado; bibliotecas usadas

Uno o más archivos .lib, pero ningún archivo .obj, se pasó al vinculador.

Dado que el vinculador no es capaz de obtener acceso a información en un archivo .lib que puede tener acceso en un archivo .obj, esta advertencia indica que tendrá que especificar explícitamente otras opciones del vinculador. Por ejemplo, tendrá que especificar el [automático](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), o [/Entry](../../build/reference/entry-entry-point-symbol.md) opciones.