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
ms.openlocfilehash: f8b1c932f53651b8ad116139724348714b183506
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939395"
---
# <a name="jitintrinsic"></a>jitintrinsic
Marca la función como significativa para Common Language Runtime de 64 bits. Se utiliza en algunas funciones de bibliotecas proporcionadas por Microsoft.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Comentarios  
 `jitintrinsic` agrega un objeto MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) a una firma de función.  
  
 No se recomienda usar los usuarios utilicen este **__declspec** modificador, como resultados inesperados puede producirse.  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)