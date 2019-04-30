---
title: Advertencia de las herramientas del vinculador LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: 62ce0a0edc7f15bc5a19e4630133976f413da35a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352663"
---
# <a name="linker-tools-warning-lnk4237"></a>Advertencia de las herramientas del vinculador LNK4237

/ SUBSYSTEM: Native especificada al importar desde 'dll'; Utilice/SUBSYSTEM: Console o/SUBSYSTEM: Windows.

[/ SUBSYSTEM: Native](../../build/reference/subsystem-specify-subsystem.md) se especificó al generar una aplicación de windows (Win32) que utiliza directamente uno o varios de los siguientes:

- kernel32.dll

- gdi32.dll

- user32.dll

- uno de lo msvcrt\* archivos DLL.

Resolver esta advertencia mediante la especificación no **/SUBSYSTEM: Native**.