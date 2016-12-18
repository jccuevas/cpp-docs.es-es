---
title: "ComPtr::As (M&#233;todo) | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::As"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "As (método)"
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::As (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Devuelve un objeto de ComPtr que representa la interfaz identificada por el parámetro de plantilla especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ ComPtr<U>* p  
) const;  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> p  
) const;  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `U`  
 La interfaz para ser representado por el parámetro `p`.  
  
 `p`  
 Un objeto ComPtr que representa la interfaz especificada por el parámetro `U`. Parámetro `p` no debe hacer referencia al objeto de ComPtr actual.  
  
## <a name="remarks"></a>Comentarios  
 La primera plantilla es el formulario que debe usar en el código. La segunda plantilla es una especialización de aplicación auxiliar interno, que admite características del lenguaje C++, como la [automática](../cpp/auto-cpp.md) palabra clave de deducción de tipos.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)