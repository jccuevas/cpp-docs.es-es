---
title: Advertencia de las herramientas del vinculador LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: e818909cc0b590b0f7727846cfd7b469e8bc0e3f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194231"
---
# <a name="linker-tools-warning-lnk4020"></a>Advertencia de las herramientas del vinculador LNK4020

> un registro de tipo en '*nombreDeArchivo*' está dañado; es posible que algunos símbolos y tipos no sean accesibles desde el depurador

El *nombre* de archivo PDB tiene un registro de tipo dañado.

Este problema suele ser secundario de otros problemas de compilación; a menos que este sea el primer problema de compilación, trate primero los otros errores y advertencias. Si este es el primer problema detectado, es posible que deba limpiar los directorios de compilación y volver a compilar el proyecto. Si utiliza procesos de compilación en paralelo, consulte si el error persiste al serializar la compilación.
