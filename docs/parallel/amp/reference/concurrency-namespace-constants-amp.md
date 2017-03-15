---
title: Constantes de espacio de nombres de simultaneidad (AMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13a8e8cd-2eec-4e60-a91d-5d271072747b
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 22ba62ab8b3b4f9d14953dbab3edd8228ea85193
ms.openlocfilehash: 852408f309c00aa284ce710a3612d0654ed7b768
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-constants-amp"></a>Constantes de espacio de nombres de simultaneidad (AMP)
|||  
|-|-|  
|[HLSL_MAX_NUM_BUFFERS (constante)](#hlsl_max_num_buffers)|[MODULENAME_MAX_LENGTH (constante)](#modulename_max_length)|  
  
##  <a name="a-namehlslmaxnumbuffersa--hlslmaxnumbuffers-constant"></a><a name="hlsl_max_num_buffers"></a>HLSL_MAX_NUM_BUFFERS (constante)  
 El número máximo de búferes permitido por DirectX.  
  
```  
static const UINT HLSL_MAX_NUM_BUFFERS = 64 + 128;  
```  
  
##  <a name="a-namemodulenamemaxlengtha--modulenamemaxlength-constant"></a><a name="modulename_max_length"></a>MODULENAME_MAX_LENGTH (constante)  
 Almacena la longitud máxima del nombre del módulo. Este valor debe ser el mismo en el compilador y el tiempo de ejecución.  
  
```  
static const UINT MODULENAME_MAX_LENGTH = 1024;  
```  
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

