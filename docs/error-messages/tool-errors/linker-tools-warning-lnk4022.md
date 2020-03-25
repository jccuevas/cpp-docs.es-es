---
title: Advertencia de las herramientas del vinculador LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 9b9ce09a7133c0bdc18957f6ade213583e9540eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194192"
---
# <a name="linker-tools-warning-lnk4022"></a>Advertencia de las herramientas del vinculador LNK4022

no se encuentra una coincidencia única para el símbolo ' Symbol '

LINK o LIB encontró varias coincidencias para el símbolo no representativo dado y no pudo resolver la ambigüedad. No se genera ningún archivo de salida (. exe,. dll,. exp o. lib). Esta advertencia va seguida de una advertencia [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) para cada símbolo duplicado y, por último, va seguida del error irrecuperable [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).

Para evitar esta advertencia, especifique el símbolo en su forma representativa. Ejecute [dumpbin](../../build/reference/dumpbin-options.md) en el objeto para ver los nombres representativos.
