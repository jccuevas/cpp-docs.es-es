---
title: Registercomobject (método) | Microsoft Docs
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
ms.openlocfilehash: 61ebc6b7bfb0571ba1f2ce1957d916ecb4c790c7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010989"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject (Método)
Registra uno o más objetos COM para que otras aplicaciones pueden conectarse a ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
WRL_NOTHROW virtual HRESULT RegisterCOMObject(  
   const wchar_t* serverName,  
   IID* clsids,  
   IClassFactory** factories,  
   DWORD* cookies,  
   unsigned int count);  
  
```  
  
### <a name="parameters"></a>Parámetros  
 *Nombre de servidor*  
 Nombre completo de un servidor.  
  
 *CLSID*  
 Una matriz de CLSID para registrar.  
  
 *generadores de*  
 Una matriz de interfaces de IUnknown de los objetos de clase cuya disponibilidad se está publicando.  
  
 *Cookies*  
 Cuando se complete la operación, una matriz de punteros a valores que identifican la clase de objetos que se registraron. Estos valores se utilizarán posteriormente revoca el registro.  
  
 *count*  
 El número de CLSID para registrar.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si ostrar; en caso contrario, un HRESULT como CO_E_OBJISREG que indica el motivo por el error en la operación.  
  
## <a name="remarks"></a>Comentarios  
 Los objetos COM se registran con el enumerador CLSCTX_LOCAL_SERVER de la enumeración CLSCTX.  
  
 El tipo de conexión para los objetos registrados se especifica mediante una combinación de actual *comflag* parámetro de plantilla y el enumerador REGCLS_SUSPENDED de la enumeración REGCLS.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)