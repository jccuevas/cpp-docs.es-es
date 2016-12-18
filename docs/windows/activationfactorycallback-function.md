---
title: "ActivationFactoryCallback (Funci&#243;n) | Microsoft Docs"
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
  - "module/Microsoft::WRL::Details::ActivationFactoryCallback"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivationFactoryCallback (función)"
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactoryCallback (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(  
   HSTRING activationId,  
   IActivationFactory **ppFactory  
);  
```  
  
#### Parámetros  
 `activationId`  
 Identificador de una cadena que especifica el nombre de clase en tiempo de ejecución.  
  
 `ppFactory`  
 Cuando esta operación finaliza, un generador de activación que corresponde al parámetro `activationId`.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que describe el error.  El error probable HRESULT es CLASS\_E\_CLASSNOTAVAILABLE y E\_INVALIDARG.  
  
## Comentarios  
 Obtiene el generador de activación para la identificación especificada de activación  
  
 El tiempo de ejecución de Windows llama a esta función de devolución de llamada para solicitar un objeto especificado por su nombre de clase en tiempo de ejecución.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)