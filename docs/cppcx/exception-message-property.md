---
title: "Exception::Message (Propiedad) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Exception::Message"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Exception::Message (Propiedad)"
ms.assetid: ad1199cd-0889-4803-ad0d-a3a7b3c51891
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Exception::Message (Propiedad)
Mensaje que describe el error.  
  
## Sintaxis  
  
```cpp  
public:property String^ Message;  
```  
  
## Valor de propiedad  
 En las excepciones que se originan en Windows en tiempo de ejecución, es una descripción del error proporcionada por el sistema.  
  
## Comentarios  
 En [!INCLUDE[win8](../cppcx/includes/win8-md.md)], esta propiedad es de solo lectura debido a que las excepciones en esa versión de Windows en tiempo de ejecución se transmiten a través de la ABI solo como valores HRESULT. En [!INCLUDE[win81](../cppcx/includes/win81-md.md)], se transmite información de excepción más completa a través de la ABI y puedes proporcionar un mensaje personalizado al que otros componentes podrán tener acceso mediante programación. Para obtener más información, consulta [Excepciones \(C\+\+\/CX\)](../cppcx/exceptions-c-cx.md).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Platform::Exception \(Clase\)](../cppcx/platform-exception-class.md)