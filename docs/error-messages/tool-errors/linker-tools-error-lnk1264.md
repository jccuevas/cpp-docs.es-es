---
title: Las herramientas del vinculador LNK1264 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1264
dev_langs:
- C++
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8232e83774dc53755b77ad9c8b3bbb2a0bcc6ae6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102754"
---
# <a name="linker-tools-error-lnk1264"></a>Error de las herramientas del vinculador LNK1264

/ LTCG: PGINSTRUMENT especificado pero no generación de código necesarios; Error de instrumentación

**/ LTCG: PGINSTRUMENT** se ha especificado, pero se encontraron archivos no .obj que se compilaron con [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentación no puede tener lugar y en el vínculo de error. Debe haber al menos un archivo .obj en la línea de comandos que se compila con **/GL** para que puedan realizarse la instrumentación.

Optimización guiada por perfiles (PGO) sólo está disponible en los compiladores de 64 bits.