---
title: "SimpleActivationFactory::GetRuntimeClassName (M&#233;todo) | Microsoft Docs"
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
  - "module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName"
dev_langs: 
  - "C++"
ms.assetid: 3aa07487-9a42-46f8-8893-37ba6315e50b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SimpleActivationFactory::GetRuntimeClassName (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el nombre de clase en tiempo de ejecución de una instancia de la clase especificada por el parámetro de plantilla de clase de `Base` .  
  
## Sintaxis  
  
```  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
#### Parámetros  
 `runtimeName`  
 Cuando esta operación finaliza, el nombre de clase en tiempo de ejecución.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que indica el error.  
  
## Comentarios  
 Si se define el \_\_WRL\_STRICT, se emite si la clase especificada por el parámetro de plantilla de clase de `Base` no se deriva de [RuntimeClass](../windows/runtimeclass-class.md), o no se configura un error validar con el valor de enumeración de WinRt o de WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) .  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [SimpleActivationFactory \(Clase\)](../windows/simpleactivationfactory-class.md)