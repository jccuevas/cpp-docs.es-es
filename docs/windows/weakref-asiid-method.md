---
title: "WeakRef::AsIID (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef::AsIID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsIID (método)"
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
caps.latest.revision: 7
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakRef::AsIID (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Establece el parámetro de puntero ComPtr especificado para representar el id. de interfaz especificado.  
  
## Sintaxis  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
#### Parámetros  
 `riid`  
 Id. de interfaz.  
  
 `ptr`  
 Cuando se completa esta operación, un objeto que representa el parámetro `riid`.  
  
## Valor devuelto  
  
-   S\_OK si esta operación es correcta; de lo contrario, un HRESULT que indica el motivo del error de la operación y `ptr` se establece en `nullptr`.  
  
-   S\_OK si esta operación es correcta, pero el objeto WeakRef actual ya se ha liberado. El parámetro `ptr` se establece en `nullptr`.  
  
-   S\_OK si esta operación se realiza correctamente, pero el objeto WeakRef actual no se deriva del parámetro `riid`. El parámetro `ptr` se establece en `nullptr`. \(Para más información, vea la sección Comentarios.\)  
  
## Comentarios  
 Se genera un error si el parámetro `riid` no se deriva de IInspectable. Este error sustituye el valor devuelto.  
  
 La primera plantilla es el formulario que debe usar en el código. La segunda plantilla \(no se muestra aquí, pero se declara en el archivo de encabezado\) es una especialización de aplicación auxiliar interna, que admite características del lenguaje C\+\+, como la palabra clave de deducción de tipos [automática](../cpp/auto-cpp.md).  
  
 A partir del SDK de Windows 10, este método no establece la instancia de WeakRef en `nullptr` si no se pudo obtener la referencia débil, por lo que debería evitar código de comprobación de errores que comprueba la WeakRef para `nullptr`. En su lugar, compruebe el HRESULT devuelto para determinar si el método fue correcto o compruebe `ptr` para `nullptr`.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [WeakRef \(Clase\)](../windows/weakref-class.md)