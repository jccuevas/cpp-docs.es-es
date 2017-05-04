---
title: "COMException::HResult (Propiedad) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::COMException::HResult"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COMException::HResult (Propiedad)"
ms.assetid: 53762ab5-ce71-4397-b7b4-8175741c838f
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# COMException::HResult (Propiedad)
HRESULT correspondiente a la excepción.  
  
## Sintaxis  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## Valor de propiedad  
 Valor HRESULT que especifica el error.  
  
## Comentarios  
 Para más información sobre cómo interpretar el valor HRESULT, vea [Estructura de los códigos de error COM](http://go.microsoft.com/fwlink/p/?LinkId=262045).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Encabezado de la subsección  
  
## Vea también  
 [Platform::COMException \(Clase\)](../cppcx/platform-comexception-class.md)