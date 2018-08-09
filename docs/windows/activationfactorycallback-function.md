---
title: ActivationFactoryCallback (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 858232702367aef62d0228f2e8653774896bd87f
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647188"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback (función)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(  
   HSTRING activationId,  
   IActivationFactory **ppFactory  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *activationId*  
 Identificador de una cadena que especifica un nombre de clase en tiempo de ejecución.  
  
 *ppFactory*  
 Cuando finalice esta operación, un generador de activación que corresponde al parámetro *activationId*.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. Valores HRESULT de error probable son CLASS_E_CLASSNOTAVAILABLE y E_INVALIDARG.  
  
## <a name="remarks"></a>Comentarios  
 Obtiene el generador de activación para el identificador de activación especificado.  
  
 El tiempo de ejecución de Windows llama a esta función de devolución de llamada para solicitar un objeto especificado por su nombre de clase en tiempo de ejecución.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)