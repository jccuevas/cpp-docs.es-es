---
title: "_com_ptr_t::GetActiveObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t.GetActiveObject"
  - "_com_ptr_t::GetActiveObject"
  - "GetActiveObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetActiveObject (método)"
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# _com_ptr_t::GetActiveObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Se adjunta a una instancia existente de un objeto, dado un **CLSID** o **ProgID**.  
  
## Sintaxis  
  
```  
  
      HRESULT GetActiveObject(  
   const CLSID& rclsid   
) throw( );  
HRESULT GetActiveObject(  
   LPCWSTR clsidString   
) throw( );  
HRESULT GetActiveObject(  
   LPCSTR clsidStringA   
) throw( );  
```  
  
#### Parámetros  
 `rclsid`  
 **CLSID** de un objeto.  
  
 `clsidString`  
 Cadena Unicode que contiene un **CLSID** \(que comienza con "**{**"\) o **ProgID**.  
  
 `clsidStringA`  
 Cadena multibyte, en la página de códigos ANSI, que contiene un **CLSID** \(que comienza con “**{**"\) o **ProgID**.  
  
## Comentarios  
 Estas funciones miembro llaman a `GetActiveObject` para recuperar un puntero a un objeto actual que se ha registrado con OLE y, después, consultan el tipo de interfaz de este puntero inteligente.  El puntero resultante se encapsula dentro de este objeto `_com_ptr_t`.  Se llama a **release** para disminuir el recuento de referencias para el puntero previamente encapsulado.  Esta rutina devuelve `HRESULT` para indicar si la operación se ha realizado de forma correcta o no.  
  
-   **GetActiveObject\(**  `rclsid`  **\)** Se adjunta a una instancia existente de un objeto, dado un **CLSID**.  
  
-   **GetActiveObject\(**  `clsidString`  **\)** Se adjunta a una instancia existente de un objeto, dada una cadena Unicode que contiene un **CLSID** \(que comienza con "**{**"\) o un **ProgID**.  
  
-   **GetActiveObject\(**  `clsidStringA`  **\)** Se adjunta a una instancia existente de un objeto, dada una cadena de caracteres multibyte que contiene un **CLSID** \(que comienza con "**{**"\) o un **ProgID**.  Llama a [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), que supone que la cadena está en la página de códigos ANSI en lugar de una página de códigos OEM.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_ptr\_t \(Clase\)](../cpp/com-ptr-t-class.md)