---
title: Advertencia de las herramientas del vinculador LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 1c9ccfe6ca201ae4deed69c7d01429c67cce4bda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298471"
---
# <a name="linker-tools-warning-lnk4022"></a>Advertencia de las herramientas del vinculador LNK4022

no se puede encontrar una coincidencia única para el símbolo 'symbol'

VÍNCULO o LIB encuentra varias coincidencias para el símbolo dado no representativo y no se pudo resolver la ambigüedad. Se genera ningún archivo de salida (.exe, .dll, .exp o .lib). Esta advertencia va seguida de una advertencia [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) para cada símbolo de duplicar y, por último, va seguido de un error irrecuperable [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Para evitar esta advertencia, especifique el símbolo en forma representativa. Ejecute [DUMPBIN](../../build/reference/dumpbin-options.md) en el objeto para ver nombres representativos.