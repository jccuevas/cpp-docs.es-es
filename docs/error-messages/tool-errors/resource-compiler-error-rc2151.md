---
title: Error del compilador de recursos RC2151 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2151
dev_langs: C++
helpviewer_keywords: RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: beabd61c64c296bf454aa94b8f915673b5f0cfca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2151"></a>Error del compilador de recursos RC2151
no se puede volver a usar las constantes de cadena  
  
 Usa el mismo valor dos veces en un **STRINGTABLE** instrucción. Asegúrese de que no mezcla superpuestos valores decimales y hexadecimales.  
  
 Cada identificador en un **STRINGTABLE** deben ser únicos. Para obtener la máxima eficacia utilice constantes contiguas que comiencen con un múltiplo de 16.