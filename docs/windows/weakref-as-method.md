---
title: "WeakRef::As (M&#233;todo) | Microsoft Docs"
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
  - "client/Microsoft::WRL::WeakRef::As"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "As (método)"
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
caps.latest.revision: 6
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakRef::As (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Establece el parámetro de puntero ComPtr especificado para representar la interfaz especificada.  
  
## Sintaxis  
  
```  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
#### Parámetros  
 `U`  
 Id. de interfaz.  
  
 `ptr`  
 Cuando se completa esta operación, un objeto que representa el parámetro `U`.  
  
## Valor devuelto  
  
-   S\_OK si esta operación es correcta; de lo contrario, un HRESULT que indica el motivo del error de la operación y `ptr` se establece en `nullptr`.  
  
-   S\_OK si esta operación es correcta, pero el objeto WeakRef actual ya se ha liberado. El parámetro `ptr` se establece en `nullptr`.  
  
-   S\_OK si esta operación se realiza correctamente, pero el objeto WeakRef actual no se deriva del parámetro `U`. El parámetro `ptr` se establece en `nullptr`.  
  
## Comentarios  
 Se genera un error si el parámetro `U` es IWeakReference, o no se deriva de IInspectable.  
  
 La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización de aplicación auxiliar interna, que admite características del lenguaje C\+\+, como palabra clave de deducción de tipos [automática](../cpp/auto-cpp.md).  
  
 A partir del SDK de Windows 10, este método no establece la instancia de WeakRef en `nullptr` si no se pudo obtener la referencia débil, por lo que debería evitar código de comprobación de errores que comprueba la WeakRef para `nullptr`. En su lugar, compruebe el HRESULT devuelto para determinar si el método fue correcto o compruebe `ptr` para `nullptr`.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [WeakRef \(Clase\)](../windows/weakref-class.md)