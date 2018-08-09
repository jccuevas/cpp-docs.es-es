---
title: Método Activationfactory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: 2a9b71aa-61c0-43f7-aa35-00f0ee0af031
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a2ed2393f25dac416cf3b6dfd1b178190d368a6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647107"
---
# <a name="activationfactoryqueryinterface-method"></a>ActivationFactory::QueryInterface (Método)
Recupera un puntero a la interfaz especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHOD(  
   QueryInterface  
)(REFIID riid, _Deref_out_ void **ppvObject);  
```  
  
### <a name="parameters"></a>Parámetros  
 *riid*  
 Id. de interfaz.  
  
 *ppvObject*  
 Cuando complete esta operación, un puntero a la interfaz especificada por el parámetro *riid*.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ActivationFactory (clase)](../windows/activationfactory-class.md)