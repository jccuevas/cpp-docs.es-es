---
title: "Module::RegisterCOMObject (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::RegisterCOMObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegisterCOMObject (método)"
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Module::RegisterCOMObject (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Registra uno o más objetos COM para que otras aplicaciones pueden conectarse a ellos.  
  
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
 Una matriz de interfaces IUnknown de los objetos de clase cuya disponibilidad se está publicando.  
  
 `cookies`  
 Cuando finaliza la operación, una matriz de punteros a valores que identifican la clase de objetos que se han registrado. Estos valores se utilizarán posteriormente revocar el registro.  
  
 `count`  
 El número de CLSID para registrar.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si consiga; en caso contrario, un valor HRESULT como CO_E_OBJISREG que indica el motivo por el error en la operación.  
  
## <a name="remarks"></a>Comentarios  
 Los objetos COM se registran con el enumerador de la enumeración CLSCTX CLSCTX_LOCAL_SERVER.  
  
 Se especifica el tipo de conexión para los objetos registrados por una combinación de actual `comflag` parámetro de plantilla y el enumerador REGCLS_SUSPENDED de la enumeración REGCLS.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)