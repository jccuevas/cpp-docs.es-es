---
title: Error de las herramientas del vinculador LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: ce5332c2812740ef0b8c7d8e9c64a095d20a4e2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641474"
---
# <a name="linker-tools-error-lnk2017"></a>Error de las herramientas del vinculador LNK2017

reubicación de 'símbolo' a 'segmento' no válido sin/LARGEADDRESSAWARE: no

Está intentando crear una imagen de 64 bits con direcciones de 32 bits. Para ello, debe:

- Use una dirección de carga fija.

- Restringir la imagen a 3 GB.

- Especificar [/LARGEADDRESSAWARE: no](../../build/reference/largeaddressaware-handle-large-addresses.md).