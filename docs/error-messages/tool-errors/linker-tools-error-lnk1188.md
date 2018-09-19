---
title: Las herramientas del vinculador LNK1188 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1188
dev_langs:
- C++
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36b31590d94d809c16ed64d16071db0919f60238
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098945"
---
# <a name="linker-tools-error-lnk1188"></a>Error de las herramientas del vinculador LNK1188

BADFIXUPSECTION:: destino de corrección no válida "symbol"; posible sección de longitud cero

Durante un vínculo de VxD, el destino de una reubicación no tenía una sección. Con LINK386 (una versión anterior), un registro OMF GROUP (generado por una directiva de grupo de MASM) puede haberse usado para combinar la sección de longitud cero con otra sección de longitud distinta de cero. El formato COFF no es compatible con la directiva de grupo y las secciones de longitud cero. Cuando LINK convierte automáticamente este tipo de objetos OMF a COFF, puede producirse este error.