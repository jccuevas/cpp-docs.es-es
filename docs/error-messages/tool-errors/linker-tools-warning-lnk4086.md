---
title: Advertencia de las herramientas del vinculador LNK4086
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: 6e012ceb5e20855353c69bbcde85fb78afad2011
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183428"
---
# <a name="linker-tools-warning-lnk4086"></a>Advertencia de las herramientas del vinculador LNK4086

el punto de entrada ' función ' no se __stdcall con ' número ' bytes de argumentos; es posible que la imagen no se ejecute

El punto de entrada de un archivo DLL debe ser `__stdcall`. Vuelva a compilar la función con la opción [/gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) o especifique `__stdcall` o WINAPI cuando defina la función.
