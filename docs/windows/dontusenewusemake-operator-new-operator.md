---
title: "DontUseNewUseMake::operator new (Operador) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator new (operador)"
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DontUseNewUseMake::operator new (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### Parámetros  
 `__unnamed0`  
 Un parámetro sin nombre que especifica el número de bytes de memoria para asignar.  
  
 `placement`  
 El tipo que se asignará.  
  
## Valor devuelto  
 Proporciona una manera de pasar argumentos adicionales si se sobrecarga el operador `new`.  
  
## Comentarios  
 Sobrecarga el operador `new` y evita que se utilizan en RuntimeClass.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [DontUseNewUseMake \(Clase\)](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)