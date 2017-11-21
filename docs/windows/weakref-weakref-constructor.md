---
title: Constructor Weakref | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef::WeakRef
dev_langs: C++
helpviewer_keywords: WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8a4b9c6648937813a02ca842407dbb07577f289f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef (Constructor)
Inicializa una nueva instancia de la clase WeakRef.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ptr`  
 Un puntero, referencia o referencia de valor r a un objeto existente que inicializa el objeto WeakRef actual.  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor inicializa un objeto WeakRef vacío. El segundo constructor inicializa un objeto de WeakRef de un puntero a la interfaz IWeakReference. El tercer constructor inicializa un objeto WeakRef desde una referencia a una ComPtr\< IWeakReference > objeto. Los constructores cuarto y quinto se inicializa un objeto de WeakRef de otro objeto de WeakRef.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [WeakRef (clase)](../windows/weakref-class.md)