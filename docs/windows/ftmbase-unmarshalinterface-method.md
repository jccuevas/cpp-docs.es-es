---
title: "FtmBase::UnmarshalInterface (M&#233;todo) | Microsoft Docs"
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
  - "ftm/Microsoft::WRL::FtmBase::UnmarshalInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UnmarshalInterface (método)"
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FtmBase::UnmarshalInterface (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa un proxy creado recientemente y devuelve un puntero de interfaz a ese proxy.  
  
## Sintaxis  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### Parámetros  
 `pStm`  
 Puntero a la secuencia de la que el puntero de interfaz debe unmarshaled.  
  
 `riid`  
 Referencia al identificador de interfaz que se unmarshaled.  
  
 `ppv`  
 Cuando esta operación finaliza, la dirección de una variable de puntero que recibe el puntero de interfaz solicitado en `riid`.  Si esta operación es correcta, \*`ppv` contiene el puntero solicitado de la interfaz de la interfaz que se unmarshaled.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, E\_NOINTERFACE o E\_FAIL.  
  
## Requisitos  
 **Encabezado:** ftm.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [FtmBase \(Clase\)](../windows/ftmbase-class.md)