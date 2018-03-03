---
title: "Module:: getactivationfactory (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d5c5ca4d470f52ff9dde862cc99b10a3459cd0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory (Método)
Obtiene un generador de activación para el módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW HRESULT GetActivationFactory(  
   _In_ HSTRING pActivatibleClassId,  
   _Deref_out_ IActivationFactory **ppIFactory,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pActivatibleClassId`  
 IID de una clase en tiempo de ejecución.  
  
 `ppIFactory`  
 IActivationFactory para la clase en tiempo de ejecución especificado.  
  
 `serverName`  
 El nombre de un subconjunto de los generadores de clases en el módulo actual. Especifique el nombre del servidor usado en el [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) macro, o especificar `nullptr` para obtener el nombre del servidor predeterminado.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, el valor HRESULT devuelto por GetActivationFactory.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
[Module (clase)](../windows/module-class.md) [ActivatableClass (Macros)](../windows/activatableclass-macros.md)