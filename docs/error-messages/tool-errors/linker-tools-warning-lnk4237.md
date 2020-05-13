---
title: Advertencia de las herramientas del vinculador LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: aaa26393f1ce76d3e1bc40e5ba4978d1bcdb4fc9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193763"
---
# <a name="linker-tools-warning-lnk4237"></a>Advertencia de las herramientas del vinculador LNK4237

/SUBSYSTEM: NATIVE especificado al importar desde ' dll '; Use/SUBSYSTEM: CONSOLE o/SUBSYSTEM: WINDOWS.

Se especificó [/Subsystem: Native](../../build/reference/subsystem-specify-subsystem.md) al compilar una aplicación de Windows (Win32) que usa directamente uno o varios de los siguientes elementos:

- kernel32.dll

- gdi32.dll

- user32.dll

- uno de los archivos dll msvcrt\*.

Para resolver esta advertencia, no especifique **/Subsystem: Native**.
