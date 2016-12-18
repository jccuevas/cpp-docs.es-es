---
title: "CComObjectStack Class | Microsoft Docs"
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
  - "ATL::CComObjectStack"
  - "ATL.CComObjectStack"
  - "ATL::CComObjectStack<Base>"
  - "ATL.CComObjectStack<Base>"
  - "CComObjectStack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectStack class"
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectStack Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase crea un objeto COM temporal y se proporciona una implementación básica de **IUnknown**.  
  
## Sintaxis  
  
```  
  
      template<  
   class Base   
>  
class CComObjectStack :  
   public Base  
```  
  
#### Parámetros  
 `Base`  
 La clase, derivadas de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), además de cualquier otra interfaz desea admitir en el objeto.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectStack::CComObjectStack](../Topic/CComObjectStack::CComObjectStack.md)|el constructor.|  
|[CComObjectStack::~CComObjectStack](../Topic/CComObjectStack::~CComObjectStack.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectStack::AddRef](../Topic/CComObjectStack::AddRef.md)|Especificado cero.  en modo de depuración, llamadas `_ASSERTE`.|  
|[CComObjectStack::QueryInterface](../Topic/CComObjectStack::QueryInterface.md)|devuelve **E\_NOINTERFACE**.  en modo de depuración, llamadas `_ASSERTE`.|  
|[CComObjectStack::Release](../Topic/CComObjectStack::Release.md)|Especificado cero.  en modo de depuración, llamadas `_ASSERTE`.  ~|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectStack::m\_hResFinalConstruct](../Topic/CComObjectStack::m_hResFinalConstruct.md)|Contiene **HRESULT** devuelto durante la construcción del objeto de `CComObjectStack` .|  
  
## Comentarios  
 `CComObjectStack` se utiliza para crear un objeto COM temporal y proporcionar el objeto una implementación básica de **IUnknown**.  Normalmente, se utiliza el objeto como una variable local dentro de una función \(es decir, insertado en la pila\).  Puesto que se destruye el objeto cuando no realizan los finals de la función, el recuento de referencias para aumentar la eficacia.  
  
 El ejemplo siguiente se muestra cómo crear un objeto COM utilizado en una función:  
  
 [!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/CPP/ccomobjectstack-class_1.cpp)]  
  
 El objeto temporal `Tempobj` se inserta en la pila y automáticamente desaparece cuando los finals de la función.  
  
## Jerarquía de herencia  
 `Base`  
  
 `CComObjectStack`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComObjectGlobal Class](../../atl/reference/ccomobjectglobal-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)