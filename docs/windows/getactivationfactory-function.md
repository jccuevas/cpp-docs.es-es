---
title: "GetActivationFactory (Funci&#243;n) | Microsoft Docs"
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
  - "module/Microsoft::WRL::Details::GetActivationFactory"
  - "client/ABI::Windows::Foundation::GetActivationFactory"
  - "client/Windows::Foundation::GetActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetActivationFactory (función)"
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetActivationFactory (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recupera un generador de activación para el tipo especificado por el parámetro de plantilla.  
  
## Sintaxis  
  
```  
template<  
   typename T  
>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
#### Parámetros  
 `T`  
 Un parámetro de plantilla que especifica el tipo de generador de activación.  
  
 `activatableClassId`  
 El nombre de la clase de generador de activación puede generar.  
  
 `factory`  
 Cuando esta operación finaliza, una referencia al generador de activación para `T`escrito.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un error HRESULT que indica el error de esta operación.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Windows::Foundation  
  
## Vea también  
 [Windows::Foundation \(Espacio de nombres\)](../Topic/Windows::Foundation%20Namespace.md)