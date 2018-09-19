---
title: AgileActivationFactory (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::AgileActivationFactory
dev_langs:
- C++
ms.assetid: fab98f32-bb93-4c0f-badb-49fbddb194b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3245c761ab998ff55ebe1c616542df79f937e9d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604549"
---
# <a name="agileactivationfactory-class"></a>AgileActivationFactory (Clase)
Representa un generador de activación de apartamento sencillo que implementa [FtmBase](../windows/ftmbase-class.md).
  
## <a name="syntax"></a>Sintaxis
  
```cpp
template <
   typename I0 = Details::Nil,
   typename I1 = Details::Nil,
   typename I2 = Details::Nil,
FactoryCacheFlags cacheFlagValue = FactoryCacheDefault>
class AgileActivationFactory :
   public ActivationFactory<Implements<FtmBase, I0>, I1, I2, cacheFlagValue>{};
```
  
## <a name="requirements"></a>Requisitos
 **Encabezado:** module.h
  
 **Espacio de nombres:** Microsoft::WRL
  
## <a name="see-also"></a>Vea también
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)  
 [ActivationFactory (clase)](../windows/activationfactory-class.md)