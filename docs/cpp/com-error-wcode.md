---
title: "_com_error::WCode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error.WCode"
  - "_com_error::WCode"
  - "WCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WCode (método)"
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::WCode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Recupera el código de error de 16 bits asignado en el `HRESULT`encapsulado.  
  
## Sintaxis  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## Valor devuelto  
 Si `HRESULT` está dentro del intervalo de 0x80040200 a 0x8004FFFF, el método **WCode** devuelve `HRESULT` menos 0x80040200; de lo contrario, devuelve cero.  
  
## Comentarios  
 El método **WCode** se usa para deshacer una asignación que tiene lugar en el código de compatibilidad COM.  El contenedor de una propiedad o método **dispinterface** llama a una rutina de soporte que empaqueta los argumentos y llama a **IDispatch::Invoke**.  Al volver, si se devuelve un error `HRESULT` de `DISP_E_EXCEPTION`, la información de error se recupera de la estructura **EXCEPINFO** pasada a **IDispatch::Invoke**.  El código de error puede ser un valor de 16 bits almacenado en el miembro `wCode` de la estructura **EXCEPINFO** o un valor completo de 32 bits del miembro **scode** de la estructura **EXCEPINFO**.  Si se devuelve un `wCode` de 16 bits, primero debe asignarse a un error `HRESULT` de 32 bits.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [\_com\_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)