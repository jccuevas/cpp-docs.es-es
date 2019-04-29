---
title: Error de las herramientas del vinculador LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: e74912780bab3056ead36ae3705f0910805228e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299015"
---
# <a name="linker-tools-error-lnk2027"></a>Error de las herramientas del vinculador LNK2027

módulo sin resolver referencia 'module'

Un archivo que se pasa al vinculador tiene una dependencia en un módulo que no se especificó con **/ASSEMBLYMODULE** ni se pasa directamente al vinculador.

Para resolver LNK2027, realice una de las siguientes acciones:

- No pase al vinculador el archivo que tiene la dependencia del módulo.

- Especifique el módulo con **/ASSEMBLYMODULE**.

- Si el módulo es un archivo .netmodule seguros, pase el módulo directamente al vinculador.

Para obtener más información, consulte [/ASSEMBLYMODULE (agregar un módulo MSIL al ensamblado)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) y [archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).