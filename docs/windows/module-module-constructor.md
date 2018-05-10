---
title: Constructor Module | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Module
dev_langs:
- C++
helpviewer_keywords:
- Module, constructor
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b31e9f1e4536bc124bba359ece10217ef8b7f253
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="modulemodule-constructor"></a>Module::Module (Constructor)
Inicializa una nueva instancia de la clase de módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Module();  
```  
  
## <a name="remarks"></a>Comentarios  
 Este constructor está protegido y no se puede llamar con la `new` palabra clave. En su lugar, llame a uno [Module:: GetModule (método)](../windows/module-getmodule-method.md) o [Module:: Create (método)](../windows/module-create-method.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)