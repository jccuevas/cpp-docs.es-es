---
title: "Guid::Guid (Constructores) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Guid::Guid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Plataforma, Guid::Guid"
  - "Guid::Guid"
ms.assetid: dfa4dcad-1c3b-481f-9f60-05141b9788d1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Guid::Guid (Constructores)
Inicializa una nueva instancia de un struct Guid.  
  
## Sintaxis  
  
```cpp  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        unsigned char d,   
        unsigned char e,   
        unsigned char f,   
        unsigned char g,   
        unsigned char h,   
        unsigned char i,   
        unsigned char j,   
        unsigned char k  
);  
  
    Guid(   
        GUID m  
);  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        Array<unsigned char>^ n  
);  
```  
  
#### Parámetros  
 `a`  
 Los cuatro primeros bytes del identificador exclusivo global \(GUID\).  
  
 `b`  
 Los dos bytes siguientes del identificador exclusivo global \(GUID\).  
  
 `c`  
 Los dos bytes siguientes del identificador exclusivo global \(GUID\).  
  
 `d`  
 El byte siguiente del identificador exclusivo global \(GUID\).  
  
 `e`  
 El byte siguiente del identificador exclusivo global \(GUID\).  
  
 `f`  
 El byte siguiente del identificador exclusivo global \(GUID\).  
  
 `g`  
 El byte siguiente del identificador exclusivo global \(GUID\).  
  
 `h`  
 El byte siguiente del identificador exclusivo global \(GUID\).  
  
 `i`  
 El byte siguiente del identificador exclusivo global \(GUID\).  
  
 `j`  
 El byte siguiente del identificador exclusivo global \(GUID\).  
  
 `k`  
 El byte siguiente del identificador exclusivo global \(GUID\).  
  
 `m`  
 Un GUID, tal como se definió.  
  
 `n`  
 Los ocho bytes restantes del identificador exclusivo global \(GUID\).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Platform::Guid \(Clase de valor\)](../cppcx/platform-guid-value-class.md)