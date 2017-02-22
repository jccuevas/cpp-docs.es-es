---
title: "Module::UnregisterObjects (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::UnregisterObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UnregisterObjects (método)"
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Module::UnregisterObjects (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Anula el registro de los objetos en el módulo especificado para que otras aplicaciones no pueden conectarse a ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT UnregisterObjects(  
   ModuleBase* module,  
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `module`  
 Puntero a un módulo.  
  
 `serverName`  
 Nombre de calificación que especifica un subconjunto de los objetos afectados por esta operación.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si esta operación se realiza correctamente; de lo contrario, un error HRESULT que indica el motivo por el error de la operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)