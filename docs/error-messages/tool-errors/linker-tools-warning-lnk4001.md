---
title: Las herramientas del vinculador LNK4001 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f684e85233c4df777a53f03f07936137c425946e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070424"
---
# <a name="linker-tools-warning-lnk4001"></a>Advertencia de las herramientas del vinculador LNK4001

ningún archivo objeto especificado; bibliotecas usadas

Uno o más archivos .lib, pero ningún archivo .obj, se pasó al vinculador.

Dado que el vinculador no es capaz de obtener acceso a información en un archivo .lib que puede tener acceso en un archivo .obj, esta advertencia indica que tendrá que especificar explícitamente otras opciones del vinculador. Por ejemplo, tendrá que especificar el [automático](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), o [/Entry](../../build/reference/entry-entry-point-symbol.md) opciones.