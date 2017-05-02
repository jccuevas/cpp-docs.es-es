---
title: "Exception::Exception (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::Exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::Exception (Constructor)"
ms.assetid: 173b434e-e3a8-41f5-904e-0e8fc0f21950
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::Exception (Constructor)
Inicializa una nueva instancia de la clase Exception.  
  
## Sintaxis  
  
```cpp  
  
Exception(int32 hresult)  
Exception(int32 hresult, ::Platform::String^ message)  
```  
  
#### Parámetros  
 `hresult`  
 Valor HRESULT de error representado por la excepción.  
  
 `message`  
 Mensaje especificado por el usuario, como texto preceptivo, asociado a la excepción. Normalmente, deberías optar por la segunda sobrecarga para proporcionar un mensaje descriptivo que sea lo más específico posible sobre cómo y por qué se ha producido el error.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)