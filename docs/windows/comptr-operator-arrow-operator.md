---
title: "ComPtr::operator-&gt; (Operador) | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::operator->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator-> (operador)"
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator-&gt; (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recupera un puntero al tipo especificado por el parámetro actual de la plantilla.  
  
## Sintaxis  
  
```  
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;  
```  
  
## Valor devuelto  
 Puntero al tipo especificado por el nombre de tipo actual de la plantilla.  
  
## Comentarios  
 Esta función auxiliar quita la sobrecarga innecesaria producida mediante la macro STDMETHOD.  Esta función muestra tipos de IUnknown privados en lugar de virtual.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ComPtr \(Clase\)](../windows/comptr-class.md)