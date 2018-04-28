---
title: MMWORD | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e97b1e58116d633519b1a780928e05862ac1771d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
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