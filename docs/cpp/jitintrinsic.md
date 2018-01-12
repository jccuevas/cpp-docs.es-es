---
title: jitintrinsic | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 451f9e534284a2daa69ddc11495f6ecc8af1ee13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="jitintrinsic"></a>jitintrinsic
Marca la función como significativa para Common Language Runtime de 64 bits. Se utiliza en algunas funciones de bibliotecas proporcionadas por Microsoft.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Comentarios  
 `jitintrinsic` agrega un objeto MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) a una firma de función.  
  
 No se recomienda a los usuarios que utilicen este modificador `__declspec`, ya que pueden producirse resultados inesperados.  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)