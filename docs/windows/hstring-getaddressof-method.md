---
title: "HString::GetAddressOf (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf"
dev_langs: 
  - "C++"
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# HString::GetAddressOf (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recupera un puntero al identificador HSTRING subyacente.  
  
## Sintaxis  
  
```  
HSTRING* GetAddressOf() throw()  
```  
  
## Valor devuelto  
 Un puntero al identificador subyacente de HSTRING.  
  
## Comentarios  
 Después de esta operación, el valor de cadena del identificador subyacente de HSTRING se destruye.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [HString \(Clase\)](../windows/hstring-class.md)