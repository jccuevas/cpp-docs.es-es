---
title: "_com_ptr_t::CreateInstance | Microsoft Docs"
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
  - "_com_ptr_t::CreateInstance"
  - "_com_ptr_t.CreateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateInstance (método)"
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::CreateInstance
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Crea una nueva instancia de un objeto, dado un **CLSID** o **ProgID**.  
  
## Sintaxis  
  
```  
  
      HRESULT CreateInstance(  
   const CLSID& rclsid,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCWSTR clsidString,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCSTR clsidStringA,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
```  
  
#### Parámetros  
 `rclsid`  
 **CLSID** de un objeto.  
  
 `clsidString`  
 Cadena Unicode que contiene un **CLSID** \(que comienza con "**{**"\) o **ProgID**.  
  
 `clsidStringA`  
 Cadena multibyte, en la página de códigos ANSI, que contiene un **CLSID** \(que comienza con “**{**"\) o **ProgID**.  
  
 `dwClsContext`  
 Contexto para el código ejecutable.  
  
 `pOuter`  
 El desconocido externo para [agregación](../atl/aggregation.md).  
  
## Comentarios  
 Estas funciones de miembro llaman a `CoCreateInstance` para crear un nuevo objeto CM y, a continuación, consultas para el tipo de interfaz de este puntero inteligente.  El puntero resultante se encapsula dentro de este objeto `_com_ptr_t`.  Se llama a **release** para disminuir el recuento de referencias para el puntero previamente encapsulado.  Esta rutina devuelve `HRESULT` para indicar si la operación se ha realizado de forma correcta o no.  
  
-   **CreateInstance\(**  `rclsid` **,**  `dwClsContext`  **\)** Crea una nueva instancia en ejecución de un objeto dado un **CLSID**.  
  
-   **CreateInstance\(**  `clsidString` **,**  `dwClsContext`  **\)** Crea una nueva instancia en ejecución de un objeto dada una cadena Unicode que contiene un **CLSID** \(que comienza por "**{**"\) o un **ProgID**.  
  
-   **CreateInstance\(**  `clsidStringA` **,**  `dwClsContext`  **\)** Crea una nueva instancia en ejecución de un objeto dada una cadena de caracteres multibyte que contiene un **CLSID** \(que comienza por "**{**"\) o un **ProgID**.  Llama a [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), que supone que la cadena está en la página de códigos ANSI en lugar de una página de códigos OEM.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_com\_ptr\_t \(Clase\)](../cpp/com-ptr-t-class.md)