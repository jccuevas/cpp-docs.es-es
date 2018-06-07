---
title: Las herramientas del vinculador LNK4020 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4020
dev_langs:
- C++
helpviewer_keywords:
- LNK4020
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e55239b90910f6c151949c53939d4f8ed7c15c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570709"
---
# <a name="linker-tools-warning-lnk4020"></a>Herramientas del vinculador LNK4020 de advertencia

> un registro de tipo de '*filename*' está dañado; algunos símbolos y tipos no estén accesibles desde el depurador

El archivo PDB *filename* tiene un registro de tipo está dañado.

Este problema suele ser secundario a otros problemas de compilación; a menos que esto sea el primer problema notificado de compilación, tratar con otros errores y advertencias de la primera. Si se trata el primer problema notificado, deberá limpiar los directorios de compilación y recompile el proyecto. Si utiliza procesos de compilación paralela, vea si el error persiste si se serializa la compilación.