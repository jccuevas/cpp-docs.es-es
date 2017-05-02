---
title: "Platform::ReCreateException (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ReCreateException"
dev_langs: 
  - "C++"
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::ReCreateException (M&#233;todo)
Este método es para uso interno únicamente y no se ha diseñado para el código del usuario. Usa el [método Exception::CreateException](../cppcx/exception-createexception-method.md) en su lugar.  
  
## Sintaxis  
  
```vb  
static Exception^ ReCreateException(int hr)  
```  
  
#### Parámetros  
  
## Valor de propiedad y valor devuelto  
 Devuelve un nuevo Platform::Exception^, según el HRESULT especificado.  
  
## Equivalente en .NET Framework  
  
## Requisitos