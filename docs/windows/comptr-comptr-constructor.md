---
title: "ComPtr::ComPtr (Constructor) | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::ComPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtr, constructor"
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::ComPtr (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Intializes una nueva instancia de la clase de ComPtr.  Las sobrecargas proporcionan predeterminado, cópielo, se mueven, y constructores de conversión.  
  
## Sintaxis  
  
```  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
#### Parámetros  
 `U`  
 Tipo del parámetro `other`.  
  
 `other`  
 Objeto de tipo `U`.  
  
## Valor devuelto  
  
## Comentarios  
 El primer constructor es el constructor predeterminado, que implictly crea un objeto vacío.  El segundo constructor especifica [\_\_nullptr](../windows/nullptr-cpp-component-extensions.md), que crea explícitamente un objeto vacío.  
  
 El tercer constructor crea un objeto del objeto especificado por un puntero.  
  
 Los cuartos y quintos constructores son constructores de copias.  El quinto constructor copia un objeto si se puede convertir al tipo actual.  
  
 Sexto y séptimos constructores son constructores de movimiento.  El séptimo constructor mueve un objeto si se puede convertir al tipo actual.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ComPtr \(Clase\)](../windows/comptr-class.md)