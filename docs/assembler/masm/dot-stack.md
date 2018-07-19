---
title: . PILA | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dab47677da8db2afca73a078b110300a017e7c8d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052305"
---
# <a name="stack"></a>.STACK
Cuando se utiliza con [. MODELO](../../assembler/masm/dot-model.md), define un segmento de pila (con el nombre del segmento de pila). Opcional `size` especifica el número de bytes de la pila (el valor predeterminado es 1.024). El `.STACK` directiva cierra automáticamente la instrucción de la pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.STACK [[size]]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)