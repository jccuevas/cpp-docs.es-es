---
title: jitintrinsic | Documentos de Microsoft
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
ms.openlocfilehash: 71cd88882ea104275e4c1a43ccf05494a859d303
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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