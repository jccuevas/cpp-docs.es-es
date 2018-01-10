---
title: alloca | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de55a211e1ac9fb87e8dee251c4667a82ab47ea8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="alloca"></a>alloca
[_alloca](../c-runtime-library/reference/alloca.md) debe ser 16 bytes alineados y además debe usar un puntero de marco.  
  
 La pila que se asigna debe incluir el espacio por debajo de él para parámetros de funciones llamadas posteriormente, como se describe en [asignación de la pila](../build/stack-allocation.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso de las pilas](../build/stack-usage.md)