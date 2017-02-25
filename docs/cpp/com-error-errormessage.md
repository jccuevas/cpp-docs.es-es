---
title: "_com_error::ErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error::ErrorMessage"
  - "_com_error.ErrorMessage"
  - "ErrorMessage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ErrorMessage (método)"
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_error::ErrorMessage
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Recupera el mensaje de cadena para `HRESULT` almacenado en el objeto `_com_error`.  
  
## Sintaxis  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## Valor devuelto  
 Devuelve el mensaje de cadena para `HRESULT` grabado dentro del objeto `_com_error`.  Si `HRESULT` es [wCode](../cpp/com-error-wcode.md) de 16 bits asignado, se devuelve un mensaje genérico “`IDispatch error #<wCode>`”.  Si no se encuentra ningún mensaje, se devuelve un mensaje genérico “`Unknown error #<hresult>`”.  La cadena devuelta es una cadena Unicode o multibyte, dependiendo del estado de la macro **\_UNICODE**.  
  
## Comentarios  
 Recupera el texto del mensaje del sistema adecuado para el `HRESULT` grabado dentro del objeto `_com_error`.  El texto del mensaje del sistema se obtiene llamando a la función de Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351).  La API `FormatMessage` asigna la cadena devuelta, que se libera cuando se destruye el objeto `_com_error`.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)