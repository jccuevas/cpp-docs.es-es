---
title: "SimpleClassFactory::CreateInstance (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::SimpleClassFactory::CreateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateInstance (método)"
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SimpleClassFactory::CreateInstance (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea una instancia de la interfaz especificada.  
  
## Sintaxis  
  
```  
  
STDMETHOD(  
   CreateInstance  
)  
   (_Inout_opt_ IUnknown* pUnkOuter,   
   REFIID riid,   
   _Deref_out_ void** ppvObject);  
```  
  
#### Parámetros  
 `pUnkOuter`  
 Debe ser `nullptr`; si no, el valor devuelto es CLASS\_E\_NOAGGREGATION.  
  
 SimpleClassFactory no admite la agregación.  Si la agregación fuera admitida y el objeto que fue creado fuera parte de un agregado, `pUnkOuter` sería puntero a la interfaz IUnknown que controla aggregate.  
  
 `riid`  
 Identificador de la interfaz del objeto creado.  
  
 `ppvObject`  
 Cuando esta operación finaliza, el puntero a una instancia del objeto especificado por el parámetro de `riid` .  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que indica el error.  
  
## Comentarios  
 Si se define el \_\_WRL\_STRICT, se emite si la clase base especificada en el parámetro de plantilla de clase no se deriva de [RuntimeClass](../windows/runtimeclass-class.md), o no se configura un error validar con el valor de enumeración de ClassicCom o de WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) .  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [SimpleClassFactory \(Clase\)](../windows/simpleclassfactory-class.md)