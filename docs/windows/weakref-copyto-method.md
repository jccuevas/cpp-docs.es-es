---
title: "WeakRef::CopyTo (M&#233;todo) | Microsoft Docs"
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
  - "client/Microsoft::WRL::WeakRef::CopyTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CopyTo (método)"
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
caps.latest.revision: 5
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakRef::CopyTo (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asigna un puntero a una interfaz, si está disponible, para la variable de puntero especificada.  
  
## Sintaxis  
  
```  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<  
   typename U  
>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
#### Parámetros  
 `U`  
 Puntero de una interfaz IInspectable. Se genera un error si `U` no se deriva de IInspectable.  
  
 `riid`  
 Id. de interfaz. Se genera un error si `riid` no se deriva de **IWeakReference**.  
  
 `ptr`  
 Puntero indirecto doble para IInspectable o IWeakReference.  
  
## Valor devuelto  
 S\_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error. Para obtener más información, vea la sección Comentarios.  
  
## Comentarios  
 Un valor devuelto de S\_OK significa que esta operación se realizó correctamente, pero no indica si la referencia débil se resolvió en una referencia segura. Si se devuelve S\_OK, pruebe que ese parámetro `p` es una referencia segura; es decir, el parámetro `p` no es igual a `nullptr`.  
  
 A partir del SDK de Windows 10, este método no establece la instancia de WeakRef en `nullptr` si no se pudo obtener la referencia débil, por lo que debería evitar el código de comprobación de errores que comprueba la WeakRef para `nullptr`. En su lugar, compruebe el HRESULT devuelto para determinar si el método fue correcto o compruebe `ptr` para `nullptr`.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [WeakRef \(Clase\)](../windows/weakref-class.md)