---
title: "ComPtr::ReleaseAndGetAddressOf (M&#233;todo) | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseAndGetAddressOf (método)"
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::ReleaseAndGetAddressOf (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Libera la interfaz asociada a este ComPtr a continuación recupera la dirección del miembro de datos de [ptr\_](../windows/comptr-ptr-data-member.md) , que contiene un puntero a la interfaz que se publicó.  
  
## Sintaxis  
  
```  
T** ReleaseAndGetAddressOf();  
```  
  
## Valor devuelto  
 La dirección del miembro de datos de [ptr\_](../windows/comptr-ptr-data-member.md) de este ComPtr.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ComPtr \(Clase\)](../windows/comptr-class.md)   
 [ComPtr::ptr\_ \(Miembro de datos\)](../windows/comptr-ptr-data-member.md)