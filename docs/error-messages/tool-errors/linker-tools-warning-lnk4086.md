---
title: Advertencia de las herramientas del vinculador LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: c6a5a0714e070e6cf3aee8efcdfbdfa07fa9ee69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399942"
---
# <a name="linker-tools-warning-lnk4086"></a>Advertencia de las herramientas del vinculador LNK4086

punto de entrada 'function' no es __stdcall con 'número' bytes de argumentos; imagen no se puede ejecutar

Debe ser el punto de entrada para un archivo DLL `__stdcall`. Vuelva a compilar la función con el [/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) opción o especificar `__stdcall` o WINAPI al definir la función.