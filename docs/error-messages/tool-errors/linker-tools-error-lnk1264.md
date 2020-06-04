---
title: Error de las herramientas del vinculador LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: 00041e677ac7b69df9981551ee3b6cc18f9eb33d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183766"
---
# <a name="linker-tools-error-lnk1264"></a>Error de las herramientas del vinculador LNK1264

Se especificó/LTCG: PGINSTRUMENT pero no se requiere generación de código; error de instrumentación

Se especificó **/LTCG: PGINSTRUMENT** pero no se encontraron archivos. obj compilados con [/GL](../../build/reference/gl-whole-program-optimization.md). No se puede llevar a cabo la instrumentación y se produjo un error en el vínculo. Debe haber al menos un archivo. obj en la línea de comandos que se compila con **/GL** para que se pueda producir la instrumentación.

La optimización guiada por perfiles (PGO) solo está disponible en los compiladores de 64 bits.
