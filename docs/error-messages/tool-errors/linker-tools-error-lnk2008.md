---
title: Las herramientas del vinculador LNK2008 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18eda06e7f133ada4de1b7ec28ac21be205a71f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086816"
---
# <a name="linker-tools-error-lnk2008"></a>Error de las herramientas del vinculador LNK2008

Destino de la corrección no está alineado 'symbol_name'

VÍNCULO puede encontrar un destino de la corrección en el archivo de objeto que no se ha alineado correctamente.

Este error puede deberse a producirlo personalizado una alineación (por ejemplo, #pragma [pack](../../preprocessor/pack.md)), [alinear](../../cpp/align-cpp.md) modificador, o mediante código de lenguaje de ensamblado que modifica la alineación.

Si el código no utiliza ninguno de los pasos anteriores, esto puede deberse al compilador.