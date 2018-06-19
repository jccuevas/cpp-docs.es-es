---
title: 'Module:: registerobjects (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterObjects
dev_langs:
- C++
helpviewer_keywords:
- RegisterObjects method
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 986dcfff49529eedd8d495f4c37e19fa2b6cb8bc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875349"
---
# <a name="moduleregisterobjects-method"></a>Module::RegisterObjects (Método)
Registra objetos COM o en tiempo de ejecución de Windows para que otras aplicaciones puedan conectarse a ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT RegisterObjects(  
   ModuleBase* module,   
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `module`  
 Una matriz de objetos COM o en tiempo de ejecución de Windows.  
  
 `serverName`  
 Nombre del servidor que creó el objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que indica el motivo por el error en la operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
## <a name="see-also"></a>Vea también
[Module (clase)](../windows/module-class.md)