---
title: "Asyncbase:: Fireprogress (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs: C++
helpviewer_keywords: FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dd7aa1d66697058d711edd38b3c2eb0679b73c07
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress (Método)
Se invoca el controlador de eventos de progreso actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `arg`  
 Método de controlador de eventos que se va a invocar.  
  
## <a name="remarks"></a>Comentarios  
 `ProgressTraits`se deriva de [ArgTraitsHelper (estructura)](../windows/argtraitshelper-structure.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)