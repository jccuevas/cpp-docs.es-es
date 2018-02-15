---
title: LOCAL (MASM) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 037baa2032902060f6dc3e7ab3e54d95dd0922aa
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="local-masm"></a>LOCAL (MASM)
En la primera directiva, dentro de una macro, **LOCAL** define las etiquetas que son únicas para cada instancia de la macro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## <a name="remarks"></a>Comentarios  
 En la segunda directiva, dentro de una definición de procedimiento (**PROC**), **LOCAL** crea variables basada en pilas que existen para la duración del procedimiento. El *etiqueta* puede ser una variable simple o una matriz que contiene *recuento* elementos.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)