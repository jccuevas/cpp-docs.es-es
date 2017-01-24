---
title: "_com_error::_com_error | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error._com_error"
  - "_com_error::_com_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_error (método)"
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::_com_error
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Construye un objeto `_com_error`.  
  
## Sintaxis  
  
```  
  
      _com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false  
) throw( );  
_com_error(  
   const _com_error& that   
) throw( );  
```  
  
#### Parámetros  
 `hr`  
 Información de `HRESULT`.  
  
 `perrinfo`  
 Objeto **IErrorInfo**.  
  
 **bool fAddRef\=false**  
 Hace que el constructor llame a AddRef en una interfaz **IErrorInfo** que no es null.  Esto proporciona un recuento de referencias correcto en el caso habitual de que la propiedad de la interfaz se pase al objeto `_com_error`, por ejemplo:  
  
```  
throw _com_error(hr, perrinfo);  
```  
  
 Si no desea que el código transfiera la propiedad al objeto `_com_error` y se requiere `AddRef` para el desplazamiento de **Release** en el destructor `_com_error`, construya el objeto como sigue:  
  
```  
_com_error err(hr, perrinfo, true);  
```  
  
 `that`  
 Objeto `_com_error` existente.  
  
## Comentarios  
 El primer constructor crea un nuevo objeto, dados `HRESULT` y un objeto **IErrorInfo** opcional.  El segundo crea una copia de un objeto `_com_error` existente.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_error \(Clase\)](../cpp/com-error-class.md)