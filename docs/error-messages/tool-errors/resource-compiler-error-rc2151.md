---
title: Error del compilador de recursos RC2151 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8349aa14de6aec96fa1b526cbcffbe79036f804d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323477"
---
# <a name="resource-compiler-error-rc2151"></a>Error del compilador de recursos RC2151
no se puede volver a usar las constantes de cadena  
  
 Usa el mismo valor dos veces en un **STRINGTABLE** instrucción. Asegúrese de que no mezcla superpuestos valores decimales y hexadecimales.  
  
 Cada identificador en un **STRINGTABLE** deben ser únicos. Para obtener la máxima eficacia utilice constantes contiguas que comiencen con un múltiplo de 16.