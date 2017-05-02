---
title: "Exception::CreateException (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::CreateException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::CreateException (Método)"
ms.assetid: 70e72bb4-3fec-478d-af3d-9ec8762d2825
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::CreateException (M&#233;todo)
Crea una excepción Platform::Exception^ a partir de un valor HRESULT especificado.  
  
## Sintaxis  
  
```cpp  
Exception^ CreateException(int32 hr)  
Exception^ CreateException(int32 hr, Platform::String^ message)  
```  
  
## Parámetros  
 hr  
 Un valor HRESULT que se obtiene normalmente de una llamada a un método COM. Si el valor es 0, que es igual a S\_OK, este método produce una excepción [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) debido a que los métodos COM que se realizan correctamente no deben producir excepciones.  
  
 message  
 Cadena que describe el error.  
  
## Valor devuelto  
 Una excepción que representa el HRESULT de error.  
  
## Comentarios  
 Utiliza este método para crear una excepción a partir de un valor HRESULT devuelto, por ejemplo, desde una llamada a un método de interfaz COM. Puedes utilizar la sobrecarga que toma un parámetro String^ para proporcionar un mensaje personalizado.  
  
 Es muy recomendable utilizar CreateException para crear una excepción fuertemente tipada en lugar de crear una excepción [Platform::COMException](../cppcx/platform-comexception-class.md) que simplemente contenga el valor HRESULT.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)