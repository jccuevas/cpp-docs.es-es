---
title: Las herramientas del vinculador LNK2017 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80af2bb6475fc37b7feba5b29bfe9c1292740286
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022455"
---
# <a name="linker-tools-error-lnk2017"></a>Error de las herramientas del vinculador LNK2017

reubicación de 'símbolo' a 'segmento' no válido sin/LARGEADDRESSAWARE: no

Está intentando crear una imagen de 64 bits con direcciones de 32 bits. Para ello, debe:

- Use una dirección de carga fija.

- Restringir la imagen a 3 GB.

- Especificar [/LARGEADDRESSAWARE: no](../../build/reference/largeaddressaware-handle-large-addresses.md).