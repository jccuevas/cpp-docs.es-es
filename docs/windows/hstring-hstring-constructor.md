---
title: "HString::HString (Constructor) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString::HString"
dev_langs: 
  - "C++"
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::HString (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa una nueva instancia de la clase HString.  
  
## Sintaxis  
  
```cpp  
  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### Parámetros  
 `hstr`  
 Un identificador de HSTRING.  
  
 `other`  
 Un objeto existente de HString.  
  
## Comentarios  
 El primer constructor inicializa un nuevo objeto de HString que está vacío.  
  
 El segundo constructor inicializa un nuevo objeto de HString al valor del parámetro existente de `other` , y después destruye el parámetro de `other` .  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HString \(Clase\)](../windows/hstring-class.md)