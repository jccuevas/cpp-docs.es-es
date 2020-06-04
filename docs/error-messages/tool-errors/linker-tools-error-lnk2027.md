---
title: Error de las herramientas del vinculador LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: 0c531f70f98a017e8b75cceddc684f99d33bc554
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194606"
---
# <a name="linker-tools-error-lnk2027"></a>Error de las herramientas del vinculador LNK2027

referencia de módulo sin resolver ' módulo '

Un archivo pasado al vinculador tiene una dependencia de un módulo que no se especificó con **/assemblymodule** ni se pasó directamente al enlazador.

Para resolver LNK2027, realice una de las acciones siguientes:

- No pase al enlazador el archivo que tiene la dependencia del módulo.

- Especifique el módulo con **/assemblymodule**.

- Si el módulo es un. netmodule seguro, pase el módulo directamente al enlazador.

Para obtener más información, vea [/assemblymodule (agregar un módulo MSIL al ensamblado)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) y [archivos. netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).
