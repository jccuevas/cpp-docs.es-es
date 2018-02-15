---
title: .STACK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 140afd2edc8a0cdb540adc7e12bf97662d5d6084
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="stack"></a>.STACK
Cuando se utiliza con [. MODELO](../../assembler/masm/dot-model.md), define un segmento de pila (con el nombre del segmento de pila). Opcional `size` especifica el número de bytes de la pila (el valor predeterminado es 1.024). El `.STACK` directiva cierra automáticamente la instrucción de la pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STACK [[size]]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)