---
title: Error de las herramientas del vinculador LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: b18a93c7434ee3d66f42829f373bd916a65369bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195180"
---
# <a name="linker-tools-error-lnk1188"></a>Error de las herramientas del vinculador LNK1188

BADFIXUPSECTION:: el destino de la corrección ' Symbol ' no es válido; posible sección de longitud cero

Durante un vínculo de VxD, el destino de una reubicación no tenía una sección. Con LINK386 (una versión anterior), puede que se haya usado un registro de grupo OMF (generado por una directiva de grupo MASM) para combinar la sección de longitud cero con otra sección de longitud distinta de cero. El formato COFF no admite la Directiva de grupo ni las secciones de longitud cero. Cuando LINK convierte automáticamente este tipo de objetos OMF a COFF, puede producirse este error.
