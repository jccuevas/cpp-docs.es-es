---
title: "ComPtr::operator= (Operador) | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= (operador)"
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator= (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asigna un valor al ComPtr actual.  
  
## Sintaxis  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <  
   typename U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### Parámetros  
 `U`  
 Una clase.  
  
 `other`  
 Un puntero, una referencia, o una referencia rvalue a un tipo o a otro ComPtr.  
  
## Valor devuelto  
 Una referencia al ComPtr actual.  
  
## Comentarios  
 La primera versión de este operador asigna un valor vacío al ComPtr actual.  
  
 En la segunda versión, si el puntero de interfaz de asignación no es igual que el puntero actual de la interfaz de ComPtr, el segundo puntero de interfaz se asigna al ComPtr actual.  
  
 En la tercera versión, el puntero de interfaz de asignación se asigna al ComPtr actual.  
  
 En la cuarta versión, si el puntero de interfaz de valor de asignación no es igual que el puntero actual de la interfaz de ComPtr, el segundo puntero de interfaz se asigna al ComPtr actual.  
  
 La quinta versión es un operador de la copia; una referencia a un ComPtr se asigna al ComPtr actual.  
  
 La sexta versión es un operador de la copia que usa la semántica de transferencia de recursos; una referencia rvalue a un ComPtr si cualquier tipo es conversión estática y después asignado al ComPtr actual.  
  
 La séptima versión es un operador de la copia que usa la semántica de transferencia de recursos; una referencia rvalue a un ComPtr de `U` con tipo es conversión estática a continuación y asignado al ComPtr actual.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ComPtr \(Clase\)](../windows/comptr-class.md)