---
title: Advertencia de las herramientas del vinculador LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 790b0fa25bbf41c38b843e1a2ea757fdc0d10b9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395110"
---
# <a name="linker-tools-warning-lnk4204"></a>Advertencia de las herramientas del vinculador LNK4204

Falta información de depuración para hacer referencia al módulo; 'filename' vinculación de objetos como si no hay información de depuración

El archivo .pdb tiene una firma errónea. El vinculador continuará vincular el objeto sin información de depuración. Puede que desee volver a compilar el archivo de objeto mediante el [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opción.

LNK4204 puede producirse si algunos de los objetos en la biblioteca hacen referencia a un archivo que ya no existe. Esto podría suceder al volver a generar la solución, por ejemplo: un archivo objeto podría ser eliminado y no recompila debido a un error de compilación. En este caso, tendrá que compilar con **/Z7**, o **/Fd**, para actualizar los objetos para hacer referencia a una único archivo por biblioteca (es decir, no el nombre del archivo .pdb de forma predeterminada).  Para obtener más información, consulte [/Fd (Nombre del archivo de base de datos del programa)](../../build/reference/fd-program-database-file-name.md).  Asegúrese de que el archivo .pdb se guarda con la biblioteca cada vez se actualiza en el sistema de control de código fuente.