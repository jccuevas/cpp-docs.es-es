---
title: XMMWORD | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- XMMWORD
dev_langs:
- C++
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8fd8e6c82a3275161e519eeead490473e8d64ab
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="xmmword"></a>XMMWORD
Se utiliza en los operandos multimedios de 128 bits con las instrucciones MMX y SSE (registros de XMM).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
XMMWORD  
```  
  
## <a name="remarks"></a>Comentarios  
 `XMMWORD` está diseñado para representar el mismo tipo que [__m128](../../cpp/m128.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
movdqa   xmm0, xmmword ptr [ebx]  
```