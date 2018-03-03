---
title: Intervalo de valores enteros | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 568bc2884f7fb9642175a006c09a218d8cbe1668
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="range-of-integer-values"></a>Intervalo de valores enteros
**ANSI 3.1.2.5** Las representaciones y los conjuntos de valores de los distintos tipos de enteros  
  
 Los enteros contienen 32 bits (cuatro bytes). Los enteros con signo se representan en forma de complemento de dos. El bit más significativo contiene el signo: 1 si es negativo y 0 si es positivo o cero. Los valores se muestran a continuación:  
  
|Tipo|Mínimo y máximo|  
|----------|-------------------------|  
|**unsigned short**|De 0 a 65535|  
|`signed short`|De -32768 a 32767|  
|`unsigned long`|De 0 a 4294967295|  
|**signed long**|De -2147483648 a 2147483647|  
  
## <a name="see-also"></a>Vea también  
 [Enteros](../c-language/integers.md)