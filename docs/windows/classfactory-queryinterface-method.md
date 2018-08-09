---
title: Método ClassFactory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: 9593881f-4585-4d70-8ca6-b328918d4d6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 640a28752a3bc37322737888ffc38706068118b4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652716"
---
# <a name="classfactoryqueryinterface-method"></a>ClassFactory::QueryInterface (Método)
Recupera un puntero a la interfaz especificada por el parámetro.  
  
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
 Cuando finalice esta operación, un puntero a la interfaz especificada por el parámetro *riid*.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ClassFactory (clase)](../windows/classfactory-class.md)