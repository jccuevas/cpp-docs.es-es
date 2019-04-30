---
title: Advertencia de las herramientas del vinculador LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: 7810fd9a97a8f6e22ad362819a024358a9f4b07c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298586"
---
# <a name="linker-tools-warning-lnk4020"></a>Advertencia de las herramientas del vinculador LNK4020

> en un registro de tipo '*filename*' está dañado; pueden que algunos símbolos y tipos de no ser accesibles desde el depurador

El archivo PDB *filename* tiene un registro de tipo está dañado.

Este problema suele ser secundario a otros problemas de compilación; a menos que este es el primer número de compilación notificadas, tratar con otros errores y advertencias de la primera. Si este es el primer problema notificado, deberá limpiar los directorios de compilación y vuelva a compilar el proyecto. Si utiliza los procesos de compilación paralela, vea si el error persiste al serializar la compilación.