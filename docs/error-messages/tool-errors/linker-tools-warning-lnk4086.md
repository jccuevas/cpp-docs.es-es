---
title: Las herramientas del vinculador LNK4086 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4086
dev_langs:
- C++
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a2ee7660f0ad78d04f7edb191929296c8d47a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079237"
---
# <a name="linker-tools-warning-lnk4086"></a>Advertencia de las herramientas del vinculador LNK4086

punto de entrada 'function' no es __stdcall con 'número' bytes de argumentos; imagen no se puede ejecutar

Debe ser el punto de entrada para un archivo DLL `__stdcall`. Vuelva a compilar la función con el [/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) opción o especificar `__stdcall` o WINAPI al definir la función.