---
title: Constructor Roinitializewrapper | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 64f2af40c671760bb8d4e667c209598c46b24665
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889215"
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