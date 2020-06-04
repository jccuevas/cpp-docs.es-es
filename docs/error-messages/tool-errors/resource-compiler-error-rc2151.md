---
title: Error del compilador de recursos RC2151
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 9d4eea92321ca8373f3ad5f121f4a8e96d878e79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191267"
---
# <a name="resource-compiler-error-rc2151"></a>Error del compilador de recursos RC2151

no se pueden volver a usar constantes de cadena

Está utilizando el mismo valor dos veces en una instrucción **stringtable** . Asegúrese de que no está mezclando valores decimales y hexadecimales superpuestos.

Cada identificador de una **stringtable** debe ser único. Para obtener la máxima eficacia, use constantes contiguas que se inician en un múltiplo de 16.
