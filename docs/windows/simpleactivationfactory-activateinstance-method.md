---
title: "SimpleActivationFactory::ActivateInstance (M&#233;todo) | Microsoft Docs"
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
  - "module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivateInstance (método)"
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SimpleActivationFactory::ActivateInstance (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea una instancia de la interfaz especificada.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   ActivateInstance  
)(_Deref_out_ IInspectable **ppvObject);  
```  
  
#### Parámetros  
 `ppvObject`  
 Cuando esta operación finaliza, el puntero a una instancia del objeto especificado por el parámetro de plantilla de clase de `Base` .  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que indica el error.  
  
## Comentarios  
 Si se define el \_\_WRL\_STRICT, se emite si la clase base especificada en el parámetro de plantilla de clase no se deriva de [RuntimeClass](../windows/runtimeclass-class.md), o no se configura un error validar con el valor de enumeración de WinRt o de WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) .  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [SimpleActivationFactory \(Clase\)](../windows/simpleactivationfactory-class.md)