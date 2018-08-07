---
title: Unregistercomobject (método) | Microsoft Docs
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
ms.openlocfilehash: c19e7b5388438b8c3c2359672360e4a2ee3001a3
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39602635"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject (Método)
Anula el registro de uno o más objetos COM, lo que impide que otras aplicaciones que se conecten a ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
### <a name="parameters"></a>Parámetros  
 *Nombre de servidor*  
 (Sin usar)  
  
 *Cookies*  
 Una matriz de punteros a valores que identifican los objetos de clase va a anular. La matriz creada por el [RegisterCOMObject](../windows/module-registercomobject-method.md) método.  
  
 *count*  
 El número de clases para anular el registro.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si esta operación se realiza correctamente; en caso contrario, un error HRESULT que indica el motivo por el error en la operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)