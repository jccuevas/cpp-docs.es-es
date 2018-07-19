---
title: 'Module:: registercomobject (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c002dd64049006c8ee74c709c585a3a9d0f253a5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873984"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject (Método)
Registra uno o varios objetos COM para que otras aplicaciones puedan conectarse a ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW virtual HRESULT RegisterCOMObject(  
   const wchar_t* serverName,  
   IID* clsids,  
   IClassFactory** factories,  
   DWORD* cookies,  
   unsigned int count);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `serverName`  
 Nombre completo de un servidor.  
  
 `clsids`  
 Una matriz de CLSID para registrar.  
  
 `factories`  
 Una matriz de interfaces de IUnknown de los objetos de clase se está publicando cuya disponibilidad.  
  
 `cookies`  
 Cuando se complete la operación, una matriz de punteros a valores que identifican la clase de objetos que se registraron. Estos valores se utilizarán posteriormente revocar el registro.  
  
 `count`  
 El número de CLSID para registrar.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si consiga; en caso contrario, un valor HRESULT como CO_E_OBJISREG que indica el motivo por el error en la operación.  
  
## <a name="remarks"></a>Comentarios  
 Los objetos COM están registrados con el enumerador CLSCTX_LOCAL_SERVER de la enumeración CLSCTX.  
  
 El tipo de conexión a los objetos registrados se especifica mediante una combinación de actual `comflag` parámetro de plantilla y el enumerador REGCLS_SUSPENDED de la enumeración REGCLS.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)