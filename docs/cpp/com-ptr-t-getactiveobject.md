---
title: _com_ptr_t::GetActiveObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::GetActiveObject
dev_langs:
- C++
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a67d571c2e5b80eaa1c095cc517872b8e3918fd6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject
**Específicos de Microsoft**  
  
 Se asocia a una instancia existente de un objeto, dado un **CLSID** o **ProgID**.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `rclsid`  
 El **CLSID** de un objeto.  
  
 `clsidString`  
 Una cadena Unicode que contiene un **CLSID** (a partir de "**{**") o un **ProgID**.  
  
 `clsidStringA`  
 Cadena multibyte, en la página de códigos ANSI, que contiene un **CLSID** (a partir de "**{**") o un **ProgID**.  
  
## <a name="remarks"></a>Comentarios  
 Estas funciones miembro llaman a `GetActiveObject` para recuperar un puntero a un objeto actual que se ha registrado con OLE y, después, consultan el tipo de interfaz de este puntero inteligente. El puntero resultante se encapsula dentro de este objeto `_com_ptr_t`. **Versión** se llama para disminuir el recuento de referencias para el puntero previamente encapsulado. Esta rutina devuelve `HRESULT` para indicar si la operación se ha realizado de forma correcta o no.  
  
-   **GetActiveObject (**`rclsid`**)** adjunta a una instancia existente de un objeto, dado un **CLSID**.  
  
-   **GetActiveObject (**`clsidString`**)** adjunta a una instancia existente de un objeto que proporciona una cadena Unicode que contiene un **CLSID** (a partir de "**{**") o un **ProgID**.  
  
-   **GetActiveObject (**`clsidStringA`**)** adjunta a una instancia existente de un objeto que proporciona una cadena de caracteres multibyte que contiene un **CLSID** (a partir de "**{**") o un **ProgID**. Llamadas [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), lo que supone que la cadena está en la página de códigos ANSI en lugar de una página de códigos OEM.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)