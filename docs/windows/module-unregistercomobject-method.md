---
title: 'Module:: unregistercomobject (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de4cc44d88f59e18f2c1644e9b27a9214ad32962
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881941"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject (Método)
Anula el registro de uno o varios objetos COM, lo que impide que otras aplicaciones conectarse a ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
#### <a name="parameters"></a>Parámetros  
 `serverName`  
 (Sin usar)  
  
 `cookies`  
 Una matriz de punteros a valores que identifican los objetos de clase se va a anular. La matriz creada por el [RegisterCOMObject](../windows/module-registercomobject-method.md) método.  
  
 `count`  
 El número de clases para anular el registro.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si esta operación se realiza correctamente; en caso contrario, un valor HRESULT que indica el motivo del error Error en la operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)