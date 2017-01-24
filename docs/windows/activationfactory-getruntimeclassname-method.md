---
title: "ActivationFactory::GetRuntimeClassName (M&#233;todo) | Microsoft Docs"
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
  - "module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRuntimeClassName (método)"
ms.assetid: 74e34f0a-9c51-4b40-89f5-45c6c5886ece
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactory::GetRuntimeClassName (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el nombre de clase del objeto en tiempo de ejecución que el ActivationFactory actual crea instancias.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
#### Parámetros  
 `runtimeName`  
 Cuando esta operación finaliza, un identificador de cadena que contiene el nombre de clase del objeto en tiempo de ejecución que el ActivationFactory actual crea instancias.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que describe el error.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ActivationFactory \(Clase\)](../windows/activationfactory-class.md)