---
title: "_com_ptr_t::QueryInterface | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t::QueryInterface"
  - "_com_ptr_t.QueryInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "QueryInterface (método)"
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::QueryInterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Llama a la función miembro `QueryInterface` de **IUnknown** en el puntero de interfaz encapsulado.  
  
## Sintaxis  
  
```  
  
      template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType*& p   
) throw ( );  
template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType** p  
) throw( );  
```  
  
#### Parámetros  
 `iid`  
 **IID** de un puntero de interfaz.  
  
 `p`  
 Puntero de interfaz sin formato.  
  
## Comentarios  
 Llama a **IUnknown::QueryInterface** en el puntero de interfaz encapsulado con el **IID** especificado y devuelve el puntero de interfaz sin formato resultante en `p`.  Esta rutina devuelve `HRESULT` para indicar si la operación se ha realizado de forma correcta o no.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_ptr\_t \(Clase\)](../cpp/com-ptr-t-class.md)