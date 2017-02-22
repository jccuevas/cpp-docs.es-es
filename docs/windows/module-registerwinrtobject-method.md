---
title: "Module::RegisterWinRTObject (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::RegisterWinRTObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegisterWinRTObject (método)"
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Module::RegisterWinRTObject (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Registra una o más [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] objetos para que otras aplicaciones puedan conectarse a ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `serverName`  
 Nombre que especifica un subconjunto de los objetos afectados por esta operación.  
  
 `activatableClassIds`  
 Una matriz de CLSID activable para registrar.  
  
 `cookie`  
 Un valor que identifica los objetos de clase que se han registrado. Este valor se utiliza posteriormente para revocar el registro.  
  
 `count`  
 El número de objetos que se va a registrar.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un error HRESULT como CO_E_OBJISREG que indica el motivo por el error en la operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)