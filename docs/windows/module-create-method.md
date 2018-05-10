---
title: 'Module:: Create (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99ede64c239909956f1f767db34a2a6a14c02314
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="modulecreate-method"></a>Module::Create (Método)
Crea una instancia de un módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW static Module& Create();  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   T callback  
);  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   _In_ T* object,  
   _In_ void (T::* method)()  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo de módulo.  
  
 `callback`  
 Se llama cuando se libera el último objeto de instancia del módulo.  
  
 `object`  
 El `object` y `method` parámetros se utilizan en combinación. Señale al último objeto de instancia cuando se libera el último objeto de instancia en el módulo.  
  
 `method`  
 El `object` y `method` parámetros se utilizan en combinación. Señala al método del último objeto de instancia cuando se libera el último objeto de instancia en el módulo.  
  
## <a name="return-value"></a>Valor devuelto  
 Referencia al módulo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
[Module (clase)](../windows/module-class.md)

 