---
title: jitintrinsic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0b114089567de06a71f15b69c556e08d1e4e9c6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404085"
---
# <a name="jitintrinsic"></a>jitintrinsic
Marca la función como significativa para Common Language Runtime de 64 bits. Se utiliza en algunas funciones de bibliotecas proporcionadas por Microsoft.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Comentarios  
 **jitintrinsic** agrega un objeto MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) a una firma de función.  
  
 No se recomienda usar los usuarios utilicen este **__declspec** modificador, como resultados inesperados puede producirse.  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)