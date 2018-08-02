---
title: Getaddressof (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 972a41d0-c2ef-4ae3-b2cd-77cc45156ac9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e11cd204c2c89c7fca9a824450d6136eb65520db
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461189"
---
# <a name="comptrgetaddressof-method"></a>ComPtr::GetAddressOf (Método)
Recupera la dirección de la [ptr_](../windows/comptr-ptr-data-member.md) miembro de datos que contiene un puntero a la interfaz representada por este **ComPtr**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
T* const* GetAddressOf() const;  
T** GetAddressOf();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 La dirección de una variable.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)