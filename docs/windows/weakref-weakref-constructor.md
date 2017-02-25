---
title: "WeakRef::WeakRef (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef::WeakRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakRef, constructor"
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# WeakRef::WeakRef (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase de WeakRef.  
  
## Sintaxis  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
#### Parámetros  
 `ptr`  
 Un puntero, una referencia, o una rvalue\- referencia a un objeto existente que inicializa el objeto actual de WeakRef.  
  
## Comentarios  
 El primer constructor inicializa un objeto vacío de WeakRef.  El segundo constructor inicializa un objeto de WeakRef de un puntero a la interfaz de IWeakReference.  El tercer constructor inicializa un objeto de WeakRef de una referencia a un objeto\< de ComPtr IWeakReference\> .  Los cuartos y quintos constructores inicializan un objeto de WeakRef de otro objeto de WeakRef.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [WeakRef \(Clase\)](../windows/weakref-class.md)