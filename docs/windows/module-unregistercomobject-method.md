---
title: "Module:: unregistercomobject (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45a6dc776feb1534cd7e58240a40cc173e7459de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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