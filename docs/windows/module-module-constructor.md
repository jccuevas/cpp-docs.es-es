---
title: "Module::Module (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::Module"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Module, constructor"
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::Module (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase de módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Module();  
```  
  
## <a name="remarks"></a>Comentarios  
 Este constructor está protegido y no se puede llamar con la `new` (palabra clave). En su lugar, llame a uno [Module:: GetModule (método)](../Topic/Module::GetModule%20Method.md) o [Module:: Create (método)](../windows/module-create-method.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [Module (clase)](../windows/module-class.md)