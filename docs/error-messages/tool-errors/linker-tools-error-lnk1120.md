---
title: Error de las herramientas del vinculador LNK1120
description: Describe el error del vinculador LNK1120, que informa del número de errores de símbolos externos no resueltos en el vínculo.
ms.date: 10/31/2019
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: 21a1ede07a69cdc065dd897715e243115529600d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626578"
---
# <a name="linker-tools-error-lnk1120"></a>Error de las herramientas del vinculador LNK1120

> *número* de externos sin resolver

El error LNK1120 informa del número de errores de [símbolos externos no resueltos](linker-tools-error-lnk2001.md#what-is-an-unresolved-external-symbol) en el vínculo actual.

Cada símbolo externo sin resolver se muestra primero mediante un error [LNK2001](linker-tools-error-lnk2001.md) u [LNK2019](linker-tools-error-lnk2019.md) . El mensaje LNK1120 se incluye en último lugar y muestra el recuento de errores de símbolos sin resolver.

> [!IMPORTANT]
> **No es necesario corregir este error.** Este error desaparece cuando se corrigen todos los errores del enlazador LNK2001 y LNK2019 antes de hacerlo en la salida de la compilación. Corrija siempre los problemas a partir del primer error indicado. Los errores posteriores pueden estar causados por otros anteriores y desaparecen cuando se corrigen los errores anteriores.
