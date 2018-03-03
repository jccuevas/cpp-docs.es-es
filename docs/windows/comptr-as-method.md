---
title: "Comptr:: As (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7edf8ebb089b3e39135edb14931197c984c6946c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptras-method"></a>ComPtr::As (Método)
Devuelve un objeto de ComPtr que representa la interfaz identificada por el parámetro de plantilla especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ ComPtr<U>* p  
) const;  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> p  
) const;  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `U`  
 La interfaz para ser representado por el parámetro `p`.  
  
 `p`  
 Un objeto de ComPtr que representa la interfaz especificada por el parámetro `U`. Parámetro `p` no debe hacer referencia al objeto de ComPtr actual.  
  
## <a name="remarks"></a>Comentarios  
 La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización de aplicación auxiliar interna, que admite características del lenguaje C++, como palabra clave de deducción de tipos [automática](../cpp/auto-cpp.md) .  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)