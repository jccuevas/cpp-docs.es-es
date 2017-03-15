---
title: "ComPtr::operator&amp; (Operador) | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::operator&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator& (operador)"
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator&amp; (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Libera la interfaz asociada a este objeto de `ComPtr` a continuación recupera la dirección del objeto de `ComPtr` .  
  
## Sintaxis  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## Valor devuelto  
 Una referencia parcial a `ComPtr`actual.  
  
## Comentarios  
 Este método difiere de [ComPtr::GetAddressOf](../Topic/ComPtr::GetAddressOf%20Method.md) en que las versiones de este método una referencia al puntero de interfaz.  Utilice `ComPtr::GetAddressOf` cuando se requiere la dirección del puntero de interfaz pero no lo desee liberar esa interfaz.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ComPtr \(Clase\)](../windows/comptr-class.md)