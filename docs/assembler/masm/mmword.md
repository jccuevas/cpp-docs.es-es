---
title: MMWORD | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0570a55dc11994e12acedb85d3ae8015abefb54c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="mmword"></a>MMWORD
Se utiliza en los operandos multimedios de 64 bits con las instrucciones MMX y SSE (registros de XMM).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
MMWORD  
```  
  
## <a name="remarks"></a>Comentarios  
 `MMWORD` es un tipo.  Antes de MMWORD que se va a agregar a MASM, una funcionalidad equivalente podría haberse obtenida con:  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 Aunque ambas instrucciones funcionan en los operandos de 64 bits, `QWORD` es el tipo de enteros sin signo de 64 bits y `MMWORD` es el tipo para un valor multimedia de 64 bits.  
  
 `MMWORD` está diseñado para representar el mismo tipo que [__m64](../../cpp/m64.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
movq     mm0, mmword ptr [ebx]  
```