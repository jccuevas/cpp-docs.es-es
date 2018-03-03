---
title: Constructor Roinitializewrapper | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5af6ca55445a5b8ed17a685cc0a81e8058a0eb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper (Constructor)
Inicializa una nueva instancia de la clase RoInitializeWrapper.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `flags`  
 Una de las enumeraciones RO_INIT_TYPE, que especifica la compatibilidad proporcionada por el tiempo de ejecución de Windows.  
  
## <a name="remarks"></a>Comentarios  
 RoInitializeWrapper (clase), invoca Windows::Foundation::Initialize (*marcas*).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HandleT (clase)](../windows/handlet-class.md)