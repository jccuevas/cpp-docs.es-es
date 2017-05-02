---
title: "Exception::HResult (Propiedad) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::HResult"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::HResult (Propiedad)"
ms.assetid: 24ef008d-6884-4b8b-9556-41bfa6e1edf1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::HResult (Propiedad)
HRESULT correspondiente a la excepción.  
  
## Sintaxis  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## Valor de propiedad  
 Valor HRESULT.  
  
## Comentarios  
 La mayoría de las excepciones comienzan como errores COM, que se devuelven como valores HRESULT. C\+\+\/CX convierte estos valores en objetos Platform::Exception^ y esta propiedad almacena el valor del código de error original.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Platform::Exception \(Clase\)](../cppcx/platform-exception-class.md)