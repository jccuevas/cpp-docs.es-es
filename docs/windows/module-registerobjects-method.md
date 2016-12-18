---
title: "Module::RegisterObjects (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::RegisterObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegisterObjects (método)"
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::RegisterObjects (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Registra COM o [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] objetos para que otras aplicaciones puedan conectarse a ellos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT RegisterObjects(  
   ModuleBase* module,   
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `module`  
 Una matriz de COM o [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] objetos.  
  
 `serverName`  
 Nombre del servidor que creó el objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; en caso contrario, un HRESULT que indica el motivo del error en la operación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
## <a name="see-also"></a>Vea también
[Module (clase)](../windows/module-class.md)