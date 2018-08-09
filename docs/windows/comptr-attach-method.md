---
title: Método Comptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: 5b911f2d-9830-4dc7-b9e3-527abd55d2c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78b5039268bd122ade815ed6040a1df546e0f293
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641335"
---
# <a name="comptrattach-method"></a>ComPtr::Attach (Método)
Esto asocia **ComPtr** con el tipo de interfaz especificado por el parámetro de tipo de plantilla actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void Attach(  
   _In_opt_ InterfaceType* other  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *other*  
 Un tipo de interfaz.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)