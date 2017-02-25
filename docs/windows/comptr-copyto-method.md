---
title: "ComPtr::CopyTo (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr::CopyTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CopyTo (método)"
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ComPtr::CopyTo (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copia la actual o la interfaz especificada asociada a este ComPtr el puntero especificado.  
  
## Sintaxis  
  
```  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  
template<  
   typename U  
>  
  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
#### Parámetros  
 `U`  
 Nombre de tipo.  
  
 `ptr`  
 Cuando esta operación finaliza, un puntero a la interfaz solicitada.  
  
 `riid`  
 Un identificador de interfaz  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que indica el error de la operación implícita de QueryInterface.  
  
## Comentarios  
 La primera función devuelve una copia de un puntero a la interfaz asociada a este ComPtr.  Esta función siempre devuelve S\_OK.  
  
 La segunda función realiza una operación de QueryInterface en la interfaz asociada a este ComPtr para la interfaz especificada por el parámetro de `riid` .  
  
 La tercera función realiza una operación de QueryInterface en la interfaz asociada a este ComPtr para la interfaz subyacente del parámetro de `U` .  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ComPtr \(Clase\)](../windows/comptr-class.md)